<template>
  <div class="movies-index">
    <div v-for="movie in movies" :key="movie.id">
      <router-link v-bind:to="`/movies/${movie.id}`">
        <h2>Title: {{ movie.title }}</h2>
      </router-link>
      <p>Year: {{ movie.year }}</p>
      <p>Plot: {{ movie.plot }}</p>
      <!-- <p>All Info: {{ movie }}</p> -->
      <p>Director: {{ movie.director }}</p>
      <p>English: {{ movie.english }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Here are all movies!",
      movies: [],
    };
  },
  created: function () {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      axios.get("http://localhost:3000/movies").then((response) => {
        this.movies = response.data;
        console.log("All movies:", this.recipes);
      });
    },
  },
};
</script>
