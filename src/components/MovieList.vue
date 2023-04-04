<template>
  <div class="container my-3">
    <div class="card mb-4 text-center" v-for="movie in movies" :key="movie.id">
      <div class="card-header">{{ movie.name }}</div>
      <div class="card-body">
        <h5 class="card-title">{{ movie.name }}</h5>
        <p class="card-text">added at {{ formatDate(movie.date) }}</p>
        <div class="d-grid gap-2">
          <a target="_blank" :href="movie.url" class="btn btn-primary">Watch</a>
          <button @click="deleteMovie(movie.id)" class="btn btn-danger">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "movieList",
  props: {
    movies: {
      type: Array,
    },
    deleteMovie: {
      type: Function,
    },
  },
  methods: {
    formatDate: function (date) {
      return moment(date).format("DD/MM/YYYY hh:mm:ss a");
    },
  },
};
</script>

<style scoped>
.card {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(20px);
}
</style>
