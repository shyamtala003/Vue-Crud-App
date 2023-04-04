<script>
export default {
  name: "Header",
  props: {
    title: {
      type: String,
      default: "The Movie App",
    },
  },
};
</script>

<template>
  <nav class="navbar bg-dark" data-bs-theme="dark">
    <div class="container-fluid">
      <div class="navbar-brand">
        <img
          src="../assets/logo.png"
          alt="Logo"
          width="30"
          height="30"
          class="d-inline-block align-text-top"
        />
        {{ title }}
      </div>
    </div>
  </nav>
</template>

<style></style>
