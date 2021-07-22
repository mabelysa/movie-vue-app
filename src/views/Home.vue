<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <button v-on:click="createMovie()">Create Movie</button>
    <div v-for="movie in movies" :key="movie.id">
      <h2>Title: {{ movie.title }}</h2>
      <h1>Year: {{ movie.year }}</h1>
      <p>Plot: {{ movie.plot }}</p>
    </div>
  </div>
</template>
<style></style>
<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to My Movie App!",
      movies: [],
    };
  },
  created: function () {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      axios.get("http://localhost:3000/movie").then((response) => {
        this.movies = response.data;
        console.log("All Movies:", this.movies);
      });
    },
    createMovie: function () {
      console.log("Create a new movie!");

      var params = {
        title: "Spice World",
        year: "1997",
        plot: "Spice Girls Movie",
        director: "Bob Spiers",
      };
      axios
        .post("http://localhost:3000/movie", params)
        .then((response) => {
          console.log("Success!", response.data);
          this.movies.push(response.data);
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>
