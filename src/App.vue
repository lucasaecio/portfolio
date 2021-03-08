<template>
<section id="app">
    <router-view/>
</section>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    //
  }),
};
</script>

<style>

/* Animation */
.v-enter-active, .v-leave-active {
  transition: all 1s ease;
}

.v-enter, .v-leave-to {
  transform: scale(0.1);
  opacity: 0;
}
</style>