<template>
  <div class="miCard__contenedor">
    <div class="encabezado error">
      {{ this.vehiculo.tipo }} {{ this.vehiculo.marca }}
      <b>{{ this.vehiculo.patente }}</b>
    </div>
    <div class="detalles">
      <div class="operario">
        <div class="id_operario">Operario: {{ this.vehiculo.operario }}</div>
        <div class="entrega">Entrega: {{ this.vehiculo.entrega }}</div>
      </div>
      <div class="estado">
        <div class="textoEstado">{{ textoEstado }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "miCard",

  props: {
    vehiculo: Object,
  },

  data() {
    return {
      //estado: servicio, finalizar, atrazado
      textoEstado: "",
    };
  },

  mounted() {
    console.log("Montado ;)");
  },

  watch: {},

  computed: {
    textoEstado() {
      let entrega = new Date(this.vehiculo.entrega);
      let horaActual = new Date();
      let tiempoRestante;
      let text;

      console.log(entrega);
      console.log(horaActual);

      tiempoRestante = (entrega - horaActual) / 1000;

      tiempoRestante = new Date(tiempoRestante);

      console.log(tiempoRestante);

      if (tiempoRestante.getMinutes() < 0) {
        text = "Atrazado";
      } else if (tiempoRestante.getMinutes() <= 30) {
        text = "Finalizando";
      } else {
        text = "En Servicio";
      }
      return text;
    },
  },
};
</script>
