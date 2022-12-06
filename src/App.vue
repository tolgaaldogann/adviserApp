<template>
  <advice-box msg="Welcome to Your Vue.js App"/>
</template>

<script>
import AdviceBox from './components/AdviceBox.vue'

export default {
  name: 'App',
  components: {
    AdviceBox
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@400;600;700;800&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
  background: #202632;
  font-family: 'Manrope', sans-serif;
}

body {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
