<template>
<div class="main">
  <div class="botton1">
      <h4>Notes for Jake</h4>
  <button @click="setCreating" class="pure-button button-xsmall">Add A Note
  </button>
  </div>
  <form class="pure-form" v-if="creating" @submit.prevent="addTicket">
    <fieldset>
     <textarea v-model="comment"></textarea>
     <br />
     <div class="bottons2">
       <button @click="cancelCreating" class="pure-button space-right">Cancel</button>
       <button class="pure-button pure-button-primary" type="submit">Submit</button>
     </div>

    </fieldset>
   </form>
   <div v-for="ticket in tickets" v-bind:key="ticket.id">
    <div class="ticket">
     <div class="problem">
      <div class="problempart">
       <h3> Written by: {{ticket.user.firstName}} {{ticket.user.lastName}}</h3>
       <h6>{{formatDate(ticket.created)}}</h6>
      </div>
       <div class="problempart2">
        <p>{{ticket.comment}}</p>
       </div>
     </div>
    </div>
   </div>
</div>
</template>


<script>
import axios from 'axios';
import moment from 'moment';
export default {
  name: 'MyTickets',
  data() {
    return {
      creating: false,
      comment: '',
      tickets: [],
    }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    }
  },
  created() {
    this.getTickets();
  },
  methods: {
    async logout() {
      try {
        await axios.delete("/api/users");
        this.$root.$data.user = null;
      } catch (error) {
        this.$root.$data.user = null;
      }
    },
    async getTickets() {
      try {
        let response = await axios.get("/api/tickets/" + this.$route.params.id);
        this.tickets = response.data.tickets;
        return true;
      } catch (error) {
        console.log(error);
      }
    },
    time(d) {
      return moment(d).format('D MMMM YYYY, h:mm:ss a');
    },
    formatDate(date) {
      if (moment(date).diff(Date.now(), 'days') < 15)
        return moment(date).fromNow();
      else
        return moment(date).format('d MMMM YYYY');
    },
    setCreating() {
      this.creating = true;
    },
    cancelCreating() {
      this.creating = false;
    },
    async addTicket() {
      try {
        await axios.post("/api/tickets/" + this.$route.params.id, {
          comment: this.comment
        });
        this.comment = "";
        this.creating = false;
        this.getTickets();
        return true;
      } catch (error) {
        console.log(error);
      }
    },

  },

}
</script>


<style scoped>

fieldset {
  margin-left: 10%;
  margin-right: 10%;
  width: 80%;
  text-align: center;
}
textarea {
  width: 100%;
  text-align: center;

}

h3 {
  display: flex;
  font-size: 12px;
  font-weight: normal;
  background-color: #ccc;
  padding: 10px 20px;
  padding-bottom: 0px;
  margin: 0px;
}

h6 {
  color: #888;
  font-size: 10px;
  font-weight: bold;
  padding: 0px;
  border: 0px;
  margin: 0px;
  padding-left: 20px;
  padding-top: 7px;
  padding-bottom: 4px;
  background-color: #ccc;

}

h4 {
  text-align: center;
  padding-top: 20px;
  font-size: 16px;
  font-weight: normal;
}


label {
  background-color: #000;
  color: white;
  padding: 5px;
  border-radius: 30px;
  font-size: 12px;
  margin-right: 10px;
}

.problempart2 {
 padding-left: 20px;
}

h2 {
  padding-top: 50px;
}

.botton1 {
  text-align: center;
  padding: 10px;
}

.bottons2 {
  padding: 10px;
}


</style>
