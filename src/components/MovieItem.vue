<template>
  <div class="item">
    <h2 @click="$emit('movie-clicked', movie.id)">{{movie.title}}</h2>
    <h2>
      <font-awesome-icon icon="trash" @click="$emit('movie-delete', movie.id)"/>
      &nbsp;
      <font-awesome-icon icon="edit" @click="$emit('movie-edit', movie.id)" />
    </h2>
  </div>
</template>

<script>
export default {
  name: "MovieItem",
  props: ['movie']
}
</script>

<style scoped>
  .item {
    padding: 1rem 2rem;
    display: flex;
    justify-content: space-between;
  }
  h2 {
    cursor: pointer;
    padding: 0;
    margin: 0;
  }
  .fa-trash {
    color: crimson;
  }
</style>