<template>
  <div class="container">
    <h1>Home Page</h1>
    <div class="input-group mb-3">
      <button vronclick:="searchPressed" class="btn btn-outline-secondary" type="button" id="button-addon1">Search</button>
      <input type="text" class="form-control" placeholder="Enter Search term" aria-label="Example text with button addon" aria-describedby="button-addon1">
    </div>
    <hr>
    <table class="table table-striped table-bordered">
      
      <thead>
      <tr>
        
        
        <th> Movie Name</th>
        <th> Year</th>
      
      
      </tr>
      </thead>
      <tbody>
          <tr v-on:click="openDetail(movie.imdbID)" v-for="movie in movies " 
          :key="movie.imdbID">

          <td> {{movie.Title}}</td>
          <td> {{movie.Year}}</td>
          </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: 'Home',

  mounted(){
   

  },

  data(){
    return{
      movies:[],
      searchTerm:""
    }
  },


  methods:{
    openDetail:function(imdbID){
      this.$router.push('/detail/'+imdbID)

    },
    searchPressed: function(){
      fetch('http://www.omdbapi.com/?s='+this.searchTerm+'&apikey=87d10179')
      .then(response => response.json())
      .then(data => this.movies = data["Search"]);
   }

    }
  }
  

</script>
