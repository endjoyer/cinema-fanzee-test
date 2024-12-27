<template>
  <div class="movie-detail">
    <aside class="sticky-block">
      <h1>{{ movie.name }}</h1>
      <img :src="movie.poster" alt="Movie Poster" class="poster" />
      <MovieTags :movie="movie" />
    </aside>
    <section class="content-block">
      <h2>Description</h2>
      <p>{{ movie.description }}</p>
      <h2>Trivia</h2>
      <ul>
        <li v-for="trivia in movie.trivia" :key="trivia">{{ trivia }}</li>
      </ul>
      <h2>Actors</h2>
      <ul>
        <li v-for="actor in movie.actors" :key="actor.imdb_id">
          <a
            :href="`https://www.imdb.com/name/${actor.imdb_id}`"
            target="_blank"
            >{{ actor.name }}</a
          >
        </li>
      </ul>
    </section>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import MovieTags from './MovieTags.vue';

const props = defineProps({
  movie: Object,
});
</script>

<style scoped>
.movie-detail {
  display: flex;
  gap: 64px;
  color: #fff;
}

.sticky-block {
  display: flex;
  flex-direction: column;
  width: 240px;
  position: sticky;
  top: 132px;
  gap: 24px;
  align-self: flex-start;
}

.content-block {
  flex: 1;
  font-size: 14px;
  font-weight: 500;
  line-height: 16px;
  max-width: 340px;
}

.movie-detail h1,
.movie-detail h2 {
  font-size: 32px;
  font-weight: 700;
  line-height: 38px;
  margin: 0;
}

.poster {
  width: 100%;
  height: auto;
  border-radius: 8px;
}

@media (max-width: 768px) {
  .movie-detail {
    flex-direction: column;
    gap: 32px;
  }

  .sticky-block {
    width: 100%;
    position: static;
    align-items: center;
  }

  .content-block {
    max-width: 100%;
  }

  .movie-detail h1,
  .movie-detail h2 {
    font-size: 24px;
    line-height: 30px;
  }

  .tags {
    justify-content: center;
  }

  .poster {
    width: 80%;
    height: auto;
    margin: auto;
  }
}

@media (max-width: 480px) {
  .movie-detail h1,
  .movie-detail h2 {
    font-size: 20px;
    line-height: 26px;
  }
}
</style>
