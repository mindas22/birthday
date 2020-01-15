<template>
  <div id="app">
    <birthday />
  </div>
</template>

<script>
import birthday from "@/components/birthday.vue";

export default {
  name: "app",
  components: {
    birthday
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
