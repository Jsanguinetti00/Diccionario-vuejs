<template>
  <Button text="El boton porque el card aun no está" @click="mostrarLog"></Button>
  <Card></Card>
</template>

<script>
import Button from './components/Button.vue'
import Card from './components/Card.vue'
export default {
  name: 'App',
  components: {
    Button,
    Card
  },
    methods:{
      mostrarLog(){
        console.log("Si funciono");
      }
    }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
