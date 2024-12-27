<template>
  <div class="tags">
    <span :class="['tag', ratingColor]">
      <img src="/icons/star-small.svg" alt="Rating" class="icon" />
      {{ movie.rating.toFixed(1) }}
    </span>
    <span class="tag genre">
      <img src="/icons/film-small.svg" alt="Genre" class="icon" />
      {{ movie.genre }}
    </span>
    <span class="tag duration">
      <img src="/icons/clock-small.svg" alt="Duration" class="icon" />
      {{ movie.duration }}
    </span>
  </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  movie: Object,
});

const ratingColor = computed(() => {
  if (props.movie.rating < 4) return 'red';
  if (props.movie.rating < 7) return 'purple';
  return 'green';
});
</script>

<style scoped>
.tags {
  display: flex;
  gap: 8px;
}
.tag {
  display: flex;
  align-items: center;
  gap: 4px;
  padding: 4px 8px;
  border-radius: 8px;
  font-size: 12px;
  color: #fff;
}
.red {
  background-color: #e81a0c;
}
.purple {
  background-color: #b620e0;
}
.green {
  background-color: #039c55;
}
.genre {
  background-color: #2c81fb;
}
.duration {
  background-color: #702bfe;
}
.icon {
  width: 12px;
  height: 12px;
}
</style>
