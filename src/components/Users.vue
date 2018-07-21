<template lang="pug">
  div
    h1.title Listado de usuarios
    User(v-for="user in users" :user="user")
</template>

<script>
import User from './User.vue'
import axios from 'axios'

export default {
  components: { User },
  mounted() {
    axios.get('https://randomuser.me/api/?results=20')
          .then(res => this.users = res.data.results)
          .catch(err => alert('No pudimos obtener los usuarios :('))
  },
  data() {
    return {
      users: []
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
