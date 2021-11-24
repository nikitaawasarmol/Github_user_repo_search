<template>
  <div id="app">
    <Input v-model="name" />
    <load-data :userName.sync="name"/>
  </div>
</template>

<script>
import LoadData from './components/LoadData'
import Input from "./components/Input";


export default {
  name: "root-container",
  data: () => ({
    name: ''
  }),
  components: {
    Input,
    LoadData,
  
  }
};
</script>

<style>
body {
  background-color: white;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #2c3e50;
  /* width: 100%; */
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>