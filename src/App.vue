<template>
  <headerApp />
  <serviceTable />
  <resumenTabla />
</template>

<script>
import headerApp from "./components/headerApp.vue";
import serviceTable from "./components/serviceTable.vue";
import resumenTabla from "./components/resumenTabla.vue";

export default {
  name: "App",
  components: {
    serviceTable,
    headerApp,
    resumenTabla,
  },

  data() {
    return {};
  },
};
</script>

<style>
@import "assets/css/style.css";
</style>
