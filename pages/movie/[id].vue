<template>
  <div class="detail-page">
    <Header />
    <main class="content">
      <MovieDetail v-if="movie" :movie="movie" />
      <div v-else>Loading...</div>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import MovieDetail from '~/components/MovieDetail.vue';
import { useRouter, useRoute } from 'vue-router';

const movie = ref(null);
const router = useRouter();
const route = useRoute();

const fetchMovieDetail = async () => {
  try {
    const response = await fetch('/data/movieDetail.json');
    const detailData = await response.json();
    if (detailData.id === parseInt(route.params.id)) {
      movie.value = detailData;
    } else {
      const moviesResponse = await fetch('/data/movies.json');
      const moviesData = await moviesResponse.json();
      movie.value = moviesData.items.find(
        (m) => m.id === parseInt(route.params.id)
      );
    }
  } catch (error) {
    console.error('Error fetching movie data:', error);
  }
};

onMounted(fetchMovieDetail);
</script>

<style scoped>
.main-page,
.detail-page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background: rgb(30, 30, 30);
}
.content {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  padding: 132px 46px 32px;
}
</style>
