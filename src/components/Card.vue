<template>
  <div class="cardInfo">
      <h4>Word:</h4>
      <div>
          Meanings:
          <ul style='listStyle:none'>
              <li v-for="item in props" :key="item">{{ props}}</li>
          </ul>
      </div>
  </div>
</template>

<script>
export default {
    name:'Card',
    // props:{
    //     word:String,
    //     meaning: String,
    //     phonetich: String,
    //     definition: String
    // }
    
}
</script>

<style>

</style>