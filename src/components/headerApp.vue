<template>
  <header>
    <h1 class="appName">Automotriz Chillán Ltda.</h1>
    <h2 class="companyName">Sigue<sup>®</sup> Monitor de Servicio</h2>
    <h2 id="clock">{{ hours }}<span v-html="dots"></span>{{ minutes }}</h2>
  </header>
</template>

<script>
export default {
  data() {
    return {
      hours: "",
      minutes: "",
      dots: "",
    };
  },

  mounted() {
    this.setTime();
  },

  methods: {
    setTime() {
      setInterval(() => {
        const today = new Date();
        this.hours = this.check2digits(today.getHours());
        this.minutes = this.check2digits(today.getMinutes());
        //Here I do the blink with : (don't show the seconds)
        this.dots = today.getSeconds() % 2 == 0 ? ":" : "&nbsp;";
      }, 1000);
    },

    check2digits(digit) {
      return ("0" + digit).slice(-2);
    },
  },
};
</script>
