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
    AsyncComponent: defineAsyncComponent(() => import("./miCard.vue")),
  },

  methods: {
    getData: async function () {
      try {
        var response = await axios.get(
          "https://autochillan.ddns.net:4600/api/v1/api-get-tallmae",
          {
            params: {
              sessionId:
                "",
            },
          }
        );
        // console.table(response);
        this.servicios = response.data.data;
        console.log(this.servicios);
        console.log(this.servicios[0].CLAVE);
      } catch (error) {
        console.error(error);
      }
    },
  },

  data() {
    return {
      // DEBEN ENVIARME LOS DATOS ORDENADOS POR ENTREGA ASCENDENTE
      servicios: [
        {
          patente: "DTTX-37",
          marca: "Chevrolet",
          tipo: "Camioneta",
          operario: "Joaquin Concha",
          entrega: "2022/03/31 09:20:00",
        },
      ],
    };
  },

  mounted() {
    this.getData();
  },
};
</script>
