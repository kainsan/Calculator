<template>
  <div class="wrapper">
    <Screen :showNumber="showNumber" />
    <Keyboard
      @resultNumber="receiveNumber($event)"
      @arrCalc="receiveNumber($event)"
    />
  </div>
</template>

<style>
html {
  box-sizing: border-box;
  height: 100%;
}
*,
*::before,
*::after {
  box-sizing: inherit;
  margin: 0;
  padding: 0;
}
body {
  align-items: center;
  background: linear-gradient(320deg, #3a0f80, #490941);
  display: flex;
  font-family: "Dosis", sans-serif;
  font-display: swap;
  height: inherit;
  justify-content: center;
}
.wrapper {
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  background: rgba(255, 255, 255, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.34);
  flex-basis: 400px;
  height: 540px;
  padding: 20px 35px;
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

<script lang="ts">

import Screen from "../components/Screen.vue";
import Keyboard from "../components/Keyboard.vue";
export default {
  components: {
    Screen,
    Keyboard,
  },
  data() {
    return {
      showNumber: "0",
    };
  },
  methods: {
    receiveNumber(value: any) {
      if (value.length) {
        this.showNumber = value.toString().replaceAll(",", "");
      } else {
        this.showNumber = value.toString();
      }
    },
  },
};
</script>
