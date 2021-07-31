<template>
  <div class="details">
    <h1>Detail Page</h1>
    <div class = "card p-3 mt-3" v-if="movie">
      <h3>{{movie.Title}}</h3>
    </div>
    
  </div>
</template>

<script>

export default {
  name: 'Detail',
  mounted(){
  var imdbID = this.$route.params.imdbID;
  fetch('http://www.omdbapi.com/?i='+imdbID+'&apikey=87d10179')
  .then(response => response.json())
  .then(data => this.movie = data);
},

data(){
  return{
    movie:null
  }
}
  
}
</script>