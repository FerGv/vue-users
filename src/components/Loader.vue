<template>
  <div class="wrapper" :class="{ show }">
    <div class="loader"></div>
  </div>
</template>

<script>
// Event Bus
import eventBus from '../eventBus';

export default {
  name: 'Loader',

  data: () => ({
    show: false,
  }),

  mounted() {
    eventBus.$on('showLoader', () => this.show = true);
    eventBus.$on('hideLoader', () => this.show = false);
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  background-color: rgba(0, 0, 0, 0.5);
  height: 100vh;
  width: 100vw;
  z-index: 1000;
  position: absolute;
  left: 0;
  top: 0;
  display: none;
  justify-content: center;
  align-items: center;
}
.wrapper.show {
  display: flex;
}
.loader {
  font-size: 5rem;
}
</style>
