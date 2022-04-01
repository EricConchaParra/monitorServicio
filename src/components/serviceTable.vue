<template>
  <content>
    <miCard
      v-for="servicio in servicios"
      :vehiculo="servicio"
      :key="servicio.patente"
    >
    </miCard>
  </content>
</template>

<script>
// import miCard from "./miCard.vue";

import { defineAsyncComponent } from "vue";
import axios from "axios";

export default {
  name: "serviceTable",
  components: {
    miCard: defineAsyncComponent(() => import("./miCard.vue")),
  },

  mounted() {
    this.getData();
  },

  methods: {
    getData: async function () {
      try {
        var response = await axios.get(
          "https://autochillan.ddns.net:4600/api/v1/api-get-tallmae?sortColum=FEC_ENTF,sortDirection=DESC",
          {
            params: {
              sessionId: "",
            },
          }
        );
        this.servicios = response.data.data;
        console.log(this.servicios);
      } catch (error) {
        console.error(error);
      }
    },
  },

  data() {
    return {
      servicios: [],
    };
  },
};
</script>
