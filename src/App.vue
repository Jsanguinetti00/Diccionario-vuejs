<template>
  <Header name="Mi diccionario Online"></Header>
  <div class="header-container">
    <Dropdowm
      label="Lenguaje"
      @selected="getSelectedValueFromDropdown"
      :defaultValue="dropdown.selectedValue"
      :dataopt="dropdown.optlang"
    ></Dropdowm>
    <InputSearch
      @on-search="getPhraseFromInput"
      @on-reset="getResetCard"
    ></InputSearch>
  </div>
  <center>
    <h2>Resultados</h2>
    <Card
      v-for="(item, index) in definitions"
      :key="index"
      :definition="item.definition"
      :example="item.example"
    ></Card>
  </center>
</template>

<script>
import Card from "./components/Card.vue";
import Dropdowm from "./components/Dropdown.vue";
import InputSearch from "./components/InputSearch.vue";
import Header from "./components/Header.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Card,
    Dropdowm,
    InputSearch,
    Header,
  },

  data() {
    return {
      dropdown: {
        selectedValue: "es",
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
      catchlang: "",
      definitions: [],
    };
  },
  methods: {
    getResetCard() {
      this.definitions = [];
    },

    /* Esta funcion es el callback que recibe o cacha los valores establecidos con el $emit en el componente hijo */
    getSelectedValueFromDropdown(value) {
      this.catchlang = value;
    },

    getPhraseFromInput(word) {
      if (word !== "") {
        axios
          .get(
            `https://api.dictionaryapi.dev/api/v2/entries/${this.catchlang}/${word}`
          )
          .then((response) => {
            console.log(response.data);
            this.definitions = response.data[0].meanings[0].definitions;
          })
          .catch((err) => {
            console.error(
              `Title ${err.response.data.title} \n Message: ${err.response.data.message}`
            );
          });
      }
      else
      {
        alert("You should type something in search input");
      }
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

.header-container {
  min-width: 100vh;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  font-size: calc(10px+2vmin);
  color: #fff;
}
</style>
