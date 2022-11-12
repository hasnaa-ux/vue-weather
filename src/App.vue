<template>
  <main>
    <entering-value></entering-value>
  </main>
</template>

<script>
import EnteringValue from "./components/EnteringValue.vue";
export default {
  components: { EnteringValue },
  data() {
    return {
     
    };
  },
};
</script>
<style>
#app {
  background-image: url('./images/back1.jfif');
  background-size: cover;
}
main {
  height: 100vh;
  padding: 20px;
  background-image: linear-gradient(to bottom,  #0000005e,#000000de)
}
</style>
