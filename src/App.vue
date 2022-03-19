<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="25%">
    <Progress/>
    <!-- <HelloWorld msg="Hello Vue in CodeSandbox!"/> -->
  </div>
</template>

<script>
import Progress from "./components/Progress1";

export default {
  name: "App",
  components: {
    Progress
  }
};
</script>

<style>
* {
  margin: 0;
  padding:  0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
