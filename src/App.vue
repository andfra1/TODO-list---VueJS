<template>
  <div id="app">
    <h1>{{this.headerText}}</h1>
    <td-add></td-add>

  </div>
</template>

<script>

import TdAdd from "./components/td-add";

export default {
  name: 'app',
  components: {
    TdAdd,
  },
  data(){
    return {
      headerText: 'VueJs TODO list'
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/todo-style.scss";
</style>
