<template>
  <div id="app">
    <nav class="navbar navbar-light" style="background-color: #e3f2fd">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">Navbar</a>
          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarNavDropdown"
            aria-controls="navbarNavDropdown"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNavDropdown">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="/">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="/about">About</a>
              </li>
              <li v-if="!isLoggedIn()" class="nav-item">
                <a class="nav-link" href="/signup">Signup</a>
              </li>
              <li v-if="!isLoggedIn()" class="nav-item">
                <a class="nav-link" href="/login">Login</a>
              </li>
              <li v-if="isLoggedIn()" class="nav-item">
                <a class="nav-link" href="/logout">Logout</a>
              </li>

              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="#"
                  id="navbarDropdownMenuLink"
                  role="button"
                  data-toggle="dropdown"
                  aria-haspopup="true"
                  aria-expanded="false"
                >
                  Movies
                </a>
                <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                  <li><a class="dropdown-item" href="/movies">All Movies</a></li>
                  <li><a class="dropdown-item" href="/movies/new">Create Movie</a></li>
                  <li><a class="dropdown-item" href="#">Something else here</a></li>
                </ul>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </nav>

    <!-- <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      |
      <router-link to="/movies">Movies</router-link>
      |
      <router-link to="/movies/new">Create</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<style>
body {
  font-family: Futura, Trebuchet MS, Arial, sans-serif !important;
  text-align: center;
  background-image: url("./assets/blue-snow.png");
}
.navbar {
  text-align: center;
}
</style>
<script>
export default {
  methods: {
    isLoggedIn: function () {
      return localStorage.getItem("jwt");
    },
  },
};
</script>
