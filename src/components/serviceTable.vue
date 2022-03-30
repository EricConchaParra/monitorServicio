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
import miCard from "./miCard.vue";

export default {
  name: "serviceTable",
  components: { miCard },

  data() {
    return {
      servicios: [
        {
          patente: "DTTX-37",
          marca: "Chevrolet",
          tipo: "Camioneta",
          operario: "Joaquin Concha",
          entrega: "2022/03/30 01:40:00",
        },
        {
          patente: "LGVJ-53",
          marca: "Great Wall",
          tipo: "Camioneta",
          operario: "Daniel Concha",
          entrega: "2022/03/30 01:05:00",
        },
        {
          patente: "AA-2323",
          marca: "Datsun",
          tipo: "Automovil",
          operario: "Juan Perez",
          entrega: "2022/03/30 16:20:00",
        },
        {
          patente: "DTTK-37",
          marca: "Jac",
          tipo: "Automovil",
          operario: "Pedro Gonzalez",
          entrega: "2022/03/30 17:20:00",
        },
      ],
    };
  },
};
</script>
