<template>
  <div class="movies-new">
    <form v-on:submit.prevent="createMovie()">
      <h1>New Movie</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Title:</label>
        <input type="text" v-model="newMovieParams.title" />
      </div>
      <div>
        <label>Year:</label>
        <input type="text" v-model="newMovieParams.year" />
      </div>
      <div>
        <label>Plot:</label>
        <textarea id="plot" type="text" v-model="newMovieParams.plot"></textarea>
        <small v-if="newMovieParams.plot.length > 50 && newMovieParams.plot.length < 100" class="text-danger">
          There are {{ 100 - newMovieParams.plot.length }} characters remaining.
        </small>
      </div>
      <div>
        <label for="director">Director:</label>
        <input id="director" type="text" name="directorname" v-model="newMovieParams.director" />
      </div>
      <div>
        <label for="english">English Movie?</label>
        <input
          id="english"
          type="checkbox"
          name="englishmovie"
          select
          v-model="newMovieParams.english"
          true-value="yes"
          false-value="no"
        />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      errors: [],
      newMovieParams: { plot: "" },
    };
  },
  methods: {
    createMovie: function () {
      console.log("Creating that movie!");
      axios.post("/movies", this.newMovieParams).then((response) => {
        this.$router.push("/movies");
        console.log(response.data);
      });
    },
  },
};
</script>
