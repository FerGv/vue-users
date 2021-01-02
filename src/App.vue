<template lang="pug">
  main
    Loader/
    Users/
</template>

<script>
// Components
import Loader from './components/Loader.vue';
import Users from './components/Users.vue';

export default {
  name: 'App',
  components: { Loader, Users },
};
</script>

<style lang="scss" scoped></style>
