<template>
<div class="notes">
  <Tickets v-if="user" />
  <Login v-else/>
</div>
</template>

<script>
import Tickets from '@/components/Tickets.vue';
import Login from '@/components/Login.vue';
import axios from 'axios';
export default {
  name: 'notes',
  components: {
    Tickets,
    Login,
  },
  async created() {
    try {
      let response = await axios.get('/api/users');
      this.$root.$data.user = response.data.user;
    } catch (error) {
      this.$root.$data.user = null;
    }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    }
  }
}
</script>
