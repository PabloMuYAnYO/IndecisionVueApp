<template>
  <indecision-app></indecision-app>
</template>

<script>
import indecisionApp from './components/IndecisionAPP.vue'

export default {
  name: 'App',
  components: {
    indecisionApp
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Rubik', sans-serif;
}
body{
  background: #FF7F50;
}
#principal{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
}
#principal img{
  height: 400px;
  width: 600px;
}
</style>
