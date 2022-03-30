<template>
  <div class="miCard__contenedor">
    <div class="encabezado">
      {{ this.vehiculo.tipo }} {{ this.vehiculo.marca }}
      <b>{{ this.vehiculo.patente }}</b>
    </div>
    <div class="detalles">
      <div class="operario">
        <div class="id_operario">Operario: {{ this.vehiculo.operario }}</div>
        <div class="entrega">Entrega: {{ entrega }}</div>
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
      let minRestante;
      let text;

      minRestante = Math.round(((entrega - horaActual) / 1000) / 60);

      // console.log("minutos restantes " + minRestante);

      if (minRestante < 0) {
        text = "Atrazado";
      } else if (minRestante <= 30) {
        text = "Finalizando";
      } else {
        text = "En Servicio";
      }
      return text;
    },

    entrega(){
      let x = this.vehiculo.entrega;
      x = new Date(x);
      
      let hours = ("0" + x.getHours()).slice(-2);
      let minutes = ("0" + x.getMinutes()).slice(-2);

      return hours + ":" + minutes;

    }
  },
};
</script>
