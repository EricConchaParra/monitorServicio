<template>
  <header>
    <h1 class="appName">Monitor de Servicio</h1>
    <h2 class="companyName">Automotriz Chillán Ltda.</h2>
    <h2 id="clock">{{ clock }}</h2>
  </header>
</template>

<script>
export default {
  data() {
    return {
      clock: setTimeout(this.startTime(), 1000),
    };
  },

  methods: {
    startTime() {
      const today = new Date();
      let h = today.getHours();
      let m = today.getMinutes();
      let s = today.getSeconds();
      m = m < 10 ? "0" + m : m;
      return h + (s % 2 == 0 ? " : " : "&nbsp;&nbsp;&nbsp;") + m;
      //Here I do the blink with : (don't show the seconds)
    },
  },
};
</script>
