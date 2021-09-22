<template>
  <div className="search_container">
    <div className="container__input">
      <input type="text" v-model="inputSearch" />
      <button 
        @click="handleSearch"
        className="button"
        >
        <font-awesome-icon
          :icon="faSearch"
        />
      </button>
    </div>

    <Button @click="handleReset" text="Reset" />
  </div>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faSearch } from '@fortawesome/free-solid-svg-icons'

import Button from "./Button.vue";
export default {
  name: "InputSearch",
  data() {
    return {
      faSearch,
      inputSearch: "",
    };
  },
  components: {
    FontAwesomeIcon,
    Button,
  },
  methods: {
    handleSearch(){
        this.$emit('on-search', this.inputSearch);
    },
    handleReset() {
      this.inputSearch = "";
      this.$emit ('on-reset');
    },
  },
};
</script>

<style scoped>
.container__input {
  display: grid;
  grid-template-columns: repeat(2, max-content);
  border-radius: 10px;
  border: 1px solid #969696;
}

.container__input:focus-within,
.container__input:hover {
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}

.input {
  width: 500px !important;
  border: none;
  outline: none;
  padding: 12px 15px;
  font-size: 1rem;
  border-radius: 10px;
}

.button {
  border: none;
  cursor: pointer;
  border-radius: 0 10px 10px 0;
  padding: 0 15px;
  color: #fff;
  background: linear-gradient(70deg, rgb(194, 113, 237), rgb(101, 73, 221));
  transition: ease-in-out 0.3s;
}

.button:hover {
  filter: brightness(125%);
}

.search_container {
  display: flex;
  justify-content: space-around;
  width: fit-content;
}
</style>