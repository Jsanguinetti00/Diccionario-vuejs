<template>
  <Button text="El boton porque el card aun no está" @click="mostrarLog"></Button>
  <Card list="{{list}}"></Card>
  <Dropdowm :dataopt="optlang"></Dropdowm>
</template>

<script>
import Button from './components/Button.vue'
import Card from './components/Card.vue'
import Dropdowm from './components/Dropdown.vue'
export default {
  name: 'App',
  components: {
    Button,
    Card,
    Dropdowm
  },
    methods:{
      mostrarLog(){
        console.log("Si funciono");
      }
    },data(){
        return{  
          optlang:[{
            value:"es",
            label: "Español"
          },
          {
            value:"en",
            label: "English"
          }]
            
        
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
