<script>
import Header from "./layout/Header.vue";
import MovieForm from "./components/MovieForm.vue";
import MovieList from "./components/MovieList.vue";
export default {
  name: "App",
  components: {
    Header,
    MovieForm,
    MovieList,
  },
  data: function () {
    return {
      movies: [],
    };
  },
  methods: {
    addMovie: function (movie) {
      this.movies.push(movie);
      localStorage.setItem("@movies", JSON.stringify(this.movies));
    },
    deleteMovie: function (id) {
      const index = this.movies.findIndex((movie) => movie.id === id);
      this.movies.splice(index, 1);
      localStorage.setItem("@movies", JSON.stringify(this.movies));
    },
  },
  mounted() {
    if (localStorage.getItem("@movies")) {
      this.movies = JSON.parse(localStorage.getItem("@movies"));
    }
  },
};
</script>

<template>
  <Header title="The Movie App"></Header>
  <main>
    <div class="container px-6 py-4 form_container">
      <MovieForm :addMovie="addMovie"></MovieForm>
      <MovieList :movies="movies" :deleteMovie="deleteMovie"></MovieList>
    </div>
  </main>
</template>

<style>
* {
  padding: 0;
  outline: 0;
  margin: 0;
  box-sizing: border-box;
}
main {
  background-image: url("./assets/lco-wg.jpg");
  background-position: center;
  background-size: cover;
  min-height: 100vh;
}
.form_container {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(12px);
}
</style>
