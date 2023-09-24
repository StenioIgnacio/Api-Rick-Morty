<template>
  <div class="home">
    <h1>Rick & Morty</h1>
      <div class="content">
      <div v-for="(character, index) in characters" :key="index">
      <img :src="character.image" alt="">
      <h1> {{character.name}} </h1>
      <h4> {{character.gender}} </h4>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: 'HomeView',
  components: {
    
  },
  data(){
    return{
      characters: []
    }
  },
  mounted(){
    this.getTodos();
  },
  methods: {
    getTodos(){
      axios.get('https://rickandmortyapi.com/api/character')
      .then(res => 
      (this.characters = res.data.results))
      .catch(e => {
        console.log(e)
      })
    }
  }
}
</script>

<style scoped>
.content{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 0px 10px;
}
</style>