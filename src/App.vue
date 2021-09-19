<template>
  <Button
    text="El boton porque el card aun no está"
    @click="mostrarLog"
  ></Button>
  <Card list="{{list}}"></Card>
  <Dropdowm
    label="Lenguaje"
    @selected="getSelectedValueFromDropdown"
    :dataopt="dropdown.optlang"
  ></Dropdowm>
</template>

<script>
import Button from "./components/Button.vue";
import Card from "./components/Card.vue";
import Dropdowm from "./components/Dropdown.vue";
export default {
  name: "App",
  components: {
    Button,
    Card,
    Dropdowm,
  },

  data() {
    return {
      dropdown: {
        selectedValue: 1,
        label: "Opciones",
        optlang: [
          {
            value: "es",
            label: "Español",
          },
          {
            value: "en",
            label: "English",
          },
        ],
      },
    };
  },
  methods: {
    mostrarLog() {
      console.log("Si funciono");
    },

    /* Esta funcion es el callback que recibe o cacha los valores establecidos con el $emit en el componente hijo */
    getSelectedValueFromDropdown(value) {
      console.log(value);
    },
  },
};
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
