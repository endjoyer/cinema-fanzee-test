<template>
  <div class="movie-card-container">
    <div
      class="movie-card"
      @mouseover="hover = true"
      @mouseleave="hover = false"
    >
      <img :src="movie.poster" alt="Movie Poster" class="poster" />
      <h3 class="title">{{ movie.name }}</h3>
      <p class="description">{{ movie.description }}</p>
      <MovieTags :movie="movie" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import MovieTags from './MovieTags.vue';

const props = defineProps({
  movie: Object,
});

const hover = ref(false);
</script>

<style scoped>
.movie-card-container {
  background-color: #702bfe;
  border-radius: 16px;
}

.movie-card {
  box-sizing: border-box;
  padding: 12px;
  width: 324px;
  height: 306px;
  background: #292d32;
  border-radius: 16px;
  transition: transform 0.3s, background 0.3s;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  cursor: pointer;
}
.movie-card:hover,
.movie-card:focus {
  transform: translate(-7px, -7px);
}

.poster {
  width: 300px;
  height: 172px;
  border-radius: 8px;
  object-fit: cover;
}
.title {
  margin: 8px 0;
  font-size: 18px;
  color: #fff;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.description {
  font-size: 14px;
  color: #ccc;
  max-height: 40px;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
</style>
