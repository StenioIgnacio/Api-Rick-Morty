<template>
  <div class="home">
    <h1>Rick & Morty</h1>
      <div class="content">
      <div v-for="(character, index) in characters" :key="index">
      <img :src="character.image" alt="">
      <h2> {{character.name}} </h2>
      <h4> {{character.species}} </h4>
      <h4> {{character.status}} </h4>
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

<style>
body {
    font-family: "Crimson Text", "Arial", serif;
    font-size: 120%;
}
.content{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 0px 10px;
}

img {
  height: 50%;
  width: 50%;
  border-radius: 1rem;
}
h1 {
  color: #2c5a52;
}
h2 {
  font-weight: bold;
  font-size: 1.2rem;
  padding: 1.2rem;
  background: #30b191;
  border-radius: 1rem;
  margin: 1rem;
}
h4 {
  margin: 1rem;
  color: #ffffff;
  background: #8b8b8b;
  border-radius: 0.4rem;
  font-weight: inherit;
  padding: 0.2rem;
}

</style>