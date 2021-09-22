<template>
  <div class="card">
      <p class="definition"> <span class="badge">Definition:</span> {{ definition }}</p>
      <hr>
      <p> <span class="badge">example:</span> {{ example }}</p>
  </div>
</template>

<script>
export default {
    name:'Card',
    props:{
        definition : String,
        example : String,
    }
}
</script>

<style scoped>
.card{
    padding: 1rem;
    width: fit-content;
    box-shadow: 0px 5px 10px 0px rgba(0, 0, 0, 30%);
    border-radius: 5px;
    transition: ease-in-out .3s;
    margin-bottom: 1rem;
}
.card:hover{
    transform: scale(1.05);
}
.badge{
    border-radius: 5px;
    padding: 1px 3px;
    background: linear-gradient(70deg, rgb(112, 175, 141), mediumseagreen);
    box-shadow: 0px 5px 10px 0px rgba(0, 0, 0, 30%);
    color: white;
}
</style>