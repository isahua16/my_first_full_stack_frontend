<template>
  <div id="app">
    <page-header></page-header>
    <insert-candy></insert-candy>
    <get-candy></get-candy>
  </div>
</template>

<script>
import InsertCandy from "@/components/InsertCandy.vue";
import PageHeader from "@/components/PageHeader.vue";
import GetCandy from "@/components/GetCandy.vue";

export default {
  components: {
    PageHeader,
    InsertCandy,
    GetCandy,
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

img {
  width: 250px;
}
</style>
