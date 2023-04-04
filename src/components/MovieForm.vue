<script>
import { v4 as uuidv4 } from "uuid";
export default {
  name: "MovieForm",
  props: {
    addMovie: {
      type: Function,
    },
  },
  data: function () {
    return {
      name: "",
      url: "",
    };
  },
  methods: {
    onSubmit: function () {
      this.addMovie({
        name: this.name,
        url: this.url,
        id: uuidv4(),
        date: Date.now(),
      });
      this.name = "";
      this.url = "";
    },
  },
};
</script>

<template>
  <form @submit.prevent="onSubmit">
    <input
      type="text"
      placeholder="enter movie name"
      required
      class="form-control my-2"
      id="inputText"
      v-model="name"
    />
    <input
      type="url"
      required
      placeholder="Enter Url"
      v-model="url"
      class="form-control my-2"
      id="inputUrl"
    />
    <div class="d-grid gap-2">
      <button type="submit" class="btn btn-primary">Add Movie</button>
    </div>
  </form>
</template>

<style></style>
