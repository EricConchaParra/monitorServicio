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
    this.scheduleGetData()
  },

  methods: {
    //Esto va a recargar los datos cada 45 seg.
    scheduleGetData: function() {
      this.getData();
      setTimeout(this.scheduleGetData, 45000);
    },
    getData: async function () {
      try {
        var response = await axios.get(
          "https://autochillan.ddns.net:4600/api/v1/api-get-tallmae?sortColum=FEC_ENTF&sortDirection=DESC",
          {
            params: {
              sessionId: "", //Obtenido desde el core
              estado: ["A"],
              fechaEntregaFinalInicio:"2022-04-01",
              fechaEntregaFinalTermino:"2022-04-01",
              rowsPerPage: 50
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
