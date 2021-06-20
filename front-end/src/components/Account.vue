<template>
<div class="accountpage">
  <div class="hero">
    <div class="heroBox">
      <div class="start-bottons">
        <p><strong>Signed in as</strong> {{user.firstName}} {{user.lastName}}</p>
        <button class="pure-button pure-button-secondary" @click="logout">Logout</button>
        <legend></legend>
      </div>
        <button class="pure-button pure-button-secondary" @click="setEditing">Edit your account</button>

      <form class="pure-form" v-if="editing" @submit.prevent="EditAccount">
        <fieldset>
          <legend></legend>
          <input placeholder="new first name" v-model="firstName">
          <button type="submit" class="pure-button pure-button-primary" @click.prevent="editFirstName">Save</button>
        </fieldset>
        <fieldset>
          <input placeholder="new last name" v-model="lastName">
          <button type="submit" class="pure-button pure-button-primary" @click.prevent="editLastName">Save</button>
        </fieldset>
        <fieldset>
            <button class="pure-button pure-button-secondary" @click="cancelEditing">Cancel</button>

        </fieldset>
      </form>
      <p v-if="error" class="error">{{error}}</p>

    </div>
  </div>
</div>

</template>

<script>
import axios from 'axios';
export default {
  name: 'AccountPage',
  props: {
    ticket: Object,
  },
  data() {
    return {
      editing: false,
      firstName: '',
      lastName: '',
      email: '',
      address: '',
      username: '',
      password: '',
      usernameLogin: '',
      passwordLogin: '',
      error: '',
      errorLogin: '',
    }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    },
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
    setEditing() {
      this.editing = true;
    },
    cancelEditing() {
      this.editing = false;
    },
  async editAddress() {
    this.error = '';
    this.errorLogin = '';
    if (!this.address){
      return;
    }
    try {
      let response = await axios.put('/api/users/' + this.user._id,{
        address: this.address,
      });
      this.$root.$data.user = response.data.user;
    } catch (error) {
      this.error = error.response.message;
      this.$root.$data.user = null;
    }
  },
  async editFirstName() {
    this.error = '';
    this.errorLogin = '';
    if (!this.firstName){
      return;
    }
    try {
      let response = await axios.put('/api/users/' + this.user._id,{
        firstName: this.firstName,
      });
      this.$root.$data.user = response.data.user;
    } catch (error) {
      this.error = error.response.message;
      this.$root.$data.user = null;
    }
  },
  async editLastName() {
    this.error = '';
    this.errorLogin = '';
    if (!this.lastName){
      return;
    }
    try {
      let response = await axios.put('/api/users/' + this.user._id,{
        lastName: this.lastName,
      });
      this.$root.$data.user = response.data.user;
    } catch (error) {
      this.error = error.response.message;
      this.$root.$data.user = null;
    }
  },
  async editEmail() {
    this.error = '';
    this.errorLogin = '';
    if (!this.email){
      return;
    }
    try {
      let response = await axios.put('/api/users/' + this.user._id,{
        email: this.email,
      });
      this.$root.$data.user = response.data.user;
    } catch (error) {
      this.error = error.response.message;
      this.$root.$data.user = null;
    }
  },

 }
}
</script>

<style scoped>
.space-above {
  margin-top: 20px;
}

h1 {
  font-size: 28px;
  font-variant: capitalize;
}

.hero {
  padding: 20px;
  display: flex;
  justify-content: center;
}

.heroBox {
  text-align: center;
}

.hero form {
  font-size: 14px;
}

.hero form legend {
  font-size: 20px;
}

input {
  margin-right: 10px;
}

.error {
  margin-top: 10px;
  display: inline;
  padding: 5px 20px;
  border-radius: 30px;
  font-size: 10px;
  background-color: #d9534f;
  color: #fff;
}
p {
  color: black;
}
.start-bottons {
  justify-content: space-between;
  margin: 15px;
}
</style>
