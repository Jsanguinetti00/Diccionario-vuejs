<template>
  <div class="dropdowncls">
    <button class="dropbtn" @click="toggle">{{ label }} {{ selectedValue.length > 0 ? `: ${selectedValue}` : '' }}</button>
    <div class="dropdown-content" :class="isActive ? 'active' : ''">
      <ul>
        <li v-for="list in dataopt" :key="list.item" value="{{list.value}}" @click="select(list.value)">
          {{ list.label }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dropdown",
  props: {
    value: String,
    label: String,
    dataopt: Array,
  },
  data(){
    return{
      isActive: false,
      selectedValue : '',
    }
  },
  methods: {
    toggle(){
      this.isActive = !this.isActive; // es para abrir y cerrar las opciones al dar click al boton de opciones
    },
    select(value){
      this.$emit('selected', value);  // de esta manera mando el valor por el callback al componente padre
      this.selectedValue = value;     // Aqui defino solamente el valor seleccionado internamente en el componente para que pueda mostrar el texto opcion :value en el botón
      this.isActive = false;          //aqui pongo el valor de selected false, para que se cierre el menu, dado por completado que seleccionaste una opcion
    }
  },
};
</script>

<style scoped>
.dropbtn {
  background: linear-gradient(70deg, rgb(194, 113, 237), rgb(101, 73, 221));
  border: none;
  border-radius: 50pt;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: white;
  font-size: 18px;
  padding: 12px;
  min-width: 200px;
  text-align: center;
  transition: ease-in-out 0.3s;
  box-shadow: 0px 5px 10px 0px rgba(0, 0, 0, 30%);
  margin: 0px 5px;
  cursor: pointer;
  outline: none
}

.dropbtn:active {
  transform: scale(0.95);
}

.dropdowncls {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  border-radius: 10pt;
  background: linear-gradient(70deg, rgb(194, 113, 237), rgb(101, 73, 221));
  min-width: 200px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
  text-align: center;
}

.dropdown-content ul {
  padding-left: 0;
}

.dropdown-content li {
  color: white;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content li:hover {
  color: black;
  background-color: #f1f1f1;
}

.dropdowncls .dropdown-content .dropdown-content,
.active {
  display: block;
}

.dropdowncls:hover .dropbtn {
  filter: brightness(125%);
}
</style>