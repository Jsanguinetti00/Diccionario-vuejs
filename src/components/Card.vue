<template>
  <div class="cardInfo" v-for="item in list" :key="item">
      <h4>Word: {{item.words}}</h4>
      <div>
          Meanings:
          <ul style='listStyle:none'>
              <li >
                  <div style='marginBottom: 10px'> <span className="badge bg-primary"> Definition: </span> {{item.definition}} </div>
                                    <div> <span className="badge bg-secondary"> Ejemplo: </span> {{item.example}} </div>
              </li>
          </ul>
      </div>
  </div>
</template>

<script>
export default {
    name:'Card',
    props:{
       
    }
}
</script>

<style>

</style>