<template>
  <div>
    <h1><font-awesome-icon icon="film" /> <span>Movie Rater</span></h1>
  </div>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>
  h1 {
    color: orange;
  }
  h1 span {
    color: white;
  }
  .fa-film {
    transform: rotate(30deg);
    font-size: 2rem;
  }
</style>