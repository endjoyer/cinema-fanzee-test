<template>
  <div class="main-page">
    <main class="content">
      <Header />
      <MovieCard
        v-for="movie in movies"
        :key="movie.id"
        :movie="movie"
        @click="goToDetail(movie.id)"
      />
      <div ref="sentinel" class="sentinel"></div>
      <!-- Sentinel for lazy loading -->
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Header from '~/components/Header.vue';
import Footer from '~/components/Footer.vue';
import MovieCard from '~/components/MovieCard.vue';
import { useRouter } from 'vue-router';

const movies = ref([]);
const allMovies = ref([]);
const router = useRouter();
const pageSize = 20; // Number of movies to load initially
const sentinel = ref(null);

const fetchMovies = async () => {
  const cachedMovies = localStorage.getItem('movies');
  if (cachedMovies) {
    allMovies.value = JSON.parse(cachedMovies);
    movies.value = allMovies.value.slice(0, pageSize);
  } else {
    const response = await fetch('/data/movies.json');
    const data = await response.json();
    allMovies.value = data.items;
    localStorage.setItem('movies', JSON.stringify(allMovies.value));
    movies.value = allMovies.value.slice(0, pageSize);
  }
};

const loadMoreMovies = () => {
  const currentLength = movies.value.length;

  if (currentLength < allMovies.value.length) {
    movies.value = movies.value.concat(
      allMovies.value.slice(currentLength, currentLength + pageSize)
    );
  }
};

const goToDetail = (id) => {
  router.push(`/movie/${id}`);
};

onMounted(() => {
  fetchMovies();

  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      loadMoreMovies();
    }
  });

  if (sentinel.value) {
    observer.observe(sentinel.value);
  }
});
</script>

<style scoped>
.main-page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background: rgb(30, 30, 30);
}

.content {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  padding: 132px 48px 32px;
  justify-content: center;
}

.sentinel {
  height: 1px;
}
</style>
