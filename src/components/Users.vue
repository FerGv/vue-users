<template lang="pug">
  .columns.is-multiline.is-centered
    .column.is-12.has-text-centered.users-nav
      .hero.is-primary
        .hero-body
          .container
            .title Users
            .button.is-info(@click="getUsers") Get users

    .users.is-12.columns.is-multiline.is-centered
      User(v-for="user in users" :user="user" :key="user.login.uuid")
</template>

<script>
// Libraries
import axios from 'axios';

// Components
import User from './User.vue';

// Event Bus
import eventBus from '../eventBus';

const API_URL = 'https://randomuser.me/api/?results=20';

export default {
  name: 'Users',
  components: { User },

  data: () => ({
    users: [],
  }),

  async mounted() {
    await this.getUsers();
  },

  methods: {
    async getUsers() {
      eventBus.$emit('showLoader');
      try {
        const res = await axios.get(API_URL);
        this.users = res.data.results;
      } catch (error) {
        console.log(error);
        alert('An error has ocurred :(');
      }
      eventBus.$emit('hideLoader');
    },
  },
};
</script>

<style lang="scss" scoped>
.users-nav {
  padding: 0;
  position: sticky;
  top: 0;
  z-index: 100;
}
.users {
  margin-top: 1rem;
  padding: 0 3rem;
}
</style>
