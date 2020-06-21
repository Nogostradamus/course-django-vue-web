<template>
  <div>
    <button @click="logout()">Logout</button>
    <div class="layout">
      <div>
        <MovieItem
          v-for="movie in movies"
          :key="movie.id"
          :movie="movie"
          @movie-clicked="movieClicked($event)"
          @movie-delete="movieDelete($event)"
          @movie-edit="movieEdit($event)"
          />
          <button @click="newMovie()">New Movie</button>
      </div>
      <MovieDetails v-if="selectedMovie" :movie="selectedMovie" @update="update()" :token="this.token"/>
      <MovieEdit v-if="editedMovie" :movie="editedMovie" @update="update()" :token="this.token"/>
    </div>
  </div>
</template>

<script>
import MovieItem from './MovieItem';
import MovieDetails from './MovieDetails';
import MovieEdit from './MovieEdit';

export default {
  name: "Movies",
  components: { MovieItem, MovieDetails, MovieEdit },
  data(){
    return {
      movies: [],
      selectedMovie: null,
      editedMovie: null,
      token: ''
    }
  },
  methods: {
    movieClicked(movie_id){
      this.editedMovie = null;
      this.selectedMovie = this.movies.find( movie => movie.id === movie_id);
    },
    movieEdit(movie_id){
      this.selectedMovie = null;
      this.editedMovie = this.movies.find( movie => movie.id === movie_id);
    },
    movieDelete(movie_id){
      fetch(`https://movie-rater-tutorial.herokuapp.com/api/movies/${movie_id}/`, {
        method: 'DELETE',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Token ${this.token}`
        }
      })
      .then( () => {
        this.movies = this.movies.filter( movie => movie.id !== movie_id);
      })
      .catch( error => console.log(error))
    },
    newMovie(){
      this.selectedMovie = null;
      this.editedMovie = {title: '', description: ''};
    },
    update(){
      this.getMovies();
    },
    getMovies(){
      fetch('https://movie-rater-tutorial.herokuapp.com/api/movies/', {
        method: 'GET',
        headers: {
          'Authorization': `Token ${this.token}`
        }
      })
      .then( resp => resp.json())
      .then( resp => {
        this.movies = resp;
        if(this.selectedMovie){
          this.selectedMovie = this.movies.find( movie => movie.id === this.selectedMovie.id);
        }
      })
     .catch( error => console.log(error))
    },
    logout(){
      this.$cookies.remove('mr-token');
      this.$router.push('/auth');
    }
  },
  created(){
    if(this.$cookies.isKey('mr-token')){
      this.token = this.$cookies.get('mr-token');
      this.getMovies();
    } else {
      this.$router.push('/auth');
    }
    
  }
}
</script>

<style scoped>
  .layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
  
</style>