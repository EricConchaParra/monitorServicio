<template>
  <div class="miCard__contenedor">
    <div class="encabezado">
      {{ this.vehiculo.vehmar.NOMBRE }} {{ this.vehiculo.vehmod.NOMBRE }}
      <b>{{ this.vehiculo.vehiculo.PATENTE }}</b>
    </div>
    <div class="detalles">
      <div class="operario">
        <div>
          <div class="id_operario">
            Asesor: {{ this.vehiculo.asesor.NOMBREUSO }}
          </div>
          <div class="entrega">Entrega: {{ this.vehiculo.HOR_ENTF }}</div>
        </div>
      </div>
      <div
        class="estado"
        :class="{ error: minutosServicio < 0, warning: minutosServicio <= 30 }"
      >
        <div>
          <div class="textoEstado">{{ textoEstado }}</div>
          <div class="tiempo">{{ controlTiempo }}</div>
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
      minutosServicio: 0,
    };
  },

  mounted() {
    // console.log("Montado ;)");
    // console.log(this.vehiculo.HOR_ENTF);
  },

  watch: {},

  computed: {
    textoEstado() {
      let hora = this.vehiculo.HOR_ENTF; //Backend devuelve solo string con la hora

      let today = new Date(); //Entonces voy a agregarle el día a mano
      let year = today.getFullYear();
      let month = today.getMonth() + 1;
      let day = today.getDate();

      let entrega = new Date(`${year}/${month}/${day} ${hora}`); //Aquí construí la fecha de hoy con la hora entrega
      let horaActual = new Date();
      let text;

      this.minutosServicio = Math.round((entrega - horaActual) / 1000 / 60);

      // console.log("minutos restantes " + this.minutosServicio);

      if (this.minutosServicio < 0) {
        text = "Atrazado";
      } else if (this.minutosServicio <= 30) {
        text = "Finalizando";
      } else {
        text = "En Servicio";
      }
      return text;
    },

    entrega() {
      let hora = this.vehiculo.HORA_ENTF; //Backend devuelve solo string con la hora
      let today = new Date();
      let year = today.getFullYear();
      let month = today.getMonth();
      let day = today.getDay();
      let entrega = new Date(`${year}/${month}/${day} ${hora}`);

      console.log(entrega);

      let hours = ("0" + x.getHours()).slice(-2);
      let minutes = ("0" + x.getMinutes()).slice(-2);

      return hours + ":" + minutes;
    },

    controlTiempo() {
      let minutos = this.minutosServicio;
      let txt;

      if (minutos < 0) {
        txt = `${minutos} min.`;
      } else if (minutos >= 30) {
        txt = "";
      } else {
        txt = `${minutos} min. restantes`;
      }
      return txt;
    },
  },
};
</script>
