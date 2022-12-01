<template>
  <div>
    <!-- <img src="./assets/logo.png" />
    <HelloWorld msg="sss" />
    <MyHome /> -->
    <CalCulator />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
// import MyHome from "./components/MyHome.vue";
import CalCulator from "./components/CalCulator.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
    // MyHome,
    CalCulator,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body{
background-color: pink;
}
</style>
