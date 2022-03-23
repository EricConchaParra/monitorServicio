<template>
  <content>
    <table>
      <tr>
        <th>Pantente</th>
        <th>Tipo Vehículo</th>
        <th>Operario</th>
        <th>Hora entrega</th>
        <th>Estado</th>
      </tr>

      <tr class="error">
        <td>LOGD-52</td>
        <td>Furgón Suzuki</td>
        <td>Daniel Concha</td>
        <td>12:20</td>
        <td>Atención</td>
      </tr>

      <tr class="warning">
        <td>DTTK-37</td>
        <td>Automovil JAC</td>
        <td>Eric Concha</td>
        <td>13:00</td>
        <td>En servicio</td>
      </tr>

      <tr>
        <td>HJSD-62</td>
        <td>Automovil Hyndai</td>
        <td>Joaquín Concha</td>
        <td>13:15</td>
        <td>En servicio</td>
      </tr>

      <tr>
        <td>DTSD-30</td>
        <td>Camioneta Great Wall</td>
        <td>Pedro Castro</td>
        <td>14:15</td>
        <td>En servicio</td>
      </tr>

      <tr>
        <td>ASDS-23</td>
        <td>Camioneta Toyota</td>
        <td>Juan Pérez</td>
        <td>14:20</td>
        <td>En servicio</td>
      </tr>

      <tr class="completed">
        <td>DTSD-27</td>
        <td>Automovil Mitsubishi</td>
        <td>Pablo Perez</td>
        <td>12:55</td>
        <td>Finalizado</td>
      </tr>

      <tr class="completed">
        <td>DTDS-22</td>
        <td>Automovil Hyndai</td>
        <td>Pedro Perez</td>
        <td>12:55</td>
        <td>Finalizado</td>
      </tr>

      <tr class="completed">
        <td>AADF-12</td>
        <td>Camioneta Mitsubishi</td>
        <td>Julián Perez</td>
        <td>12:55</td>
        <td>Finalizado</td>
      </tr>

      <tr class="completed">
        <td>DTSD-27</td>
        <td>Automovil Mitsubishi</td>
        <td>Andrés Perez</td>
        <td>12:55</td>
        <td>Finalizado</td>
      </tr>
    </table>
  </content>
</template>

<script>
export default {
  name: "serviceTable",
  props: {
    //msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
