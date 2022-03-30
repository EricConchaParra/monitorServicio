<template>
  <div class="miCard__contenedor">
    <div class="encabezado">
      {{ this.vehiculo.tipo }} {{ this.vehiculo.marca }}
      <b>{{ this.vehiculo.patente }}</b>
    </div>
    <div class="detalles">
      <div class="operario">
        <div>
          <div class="id_operario">Operario: {{ this.vehiculo.operario }}</div>
          <div class="entrega">Entrega: {{ entrega }}</div>
        </div>
      </div>
      <div class="estado" :class="{  error: minutosServicio < 0, warning: minutosServicio <= 30}">
        <div>
          <div class="textoEstado">{{ textoEstado }}</div>
          <div class="tiempo">{{controlTiempo}}</div>
        </div>
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
      minutosServicio:0,
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
      let text;

      this.minutosServicio = Math.round(((entrega - horaActual) / 1000) / 60);

      console.log("minutos restantes " + this.minutosServicio);

      if (this.minutosServicio < 0) {
        text = "Atrazado";
      } else if (this.minutosServicio <= 30) {
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

    },

    controlTiempo(){
      let minutos = this.minutosServicio;
      let txt;

      if (minutos < 0){
        txt = `${minutos} min.`
      }
      else if(minutos >= 30){
        txt = ""
      }
      else{
        txt = `${minutos} min. restantes`
      }
      return txt
    }
  },
};
</script>
