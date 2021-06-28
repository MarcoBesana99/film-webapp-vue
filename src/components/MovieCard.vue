<template>
  <div class="">
    <router-link :to="'/movie/' + movie.imdbID">
      <div>
        <div class>
          <h2 class="font-bold">{{ movie.Title }}</h2>
          <span>({{ movie.Year }})</span>
        </div>
        <div class="relative mt-3 image-container">
          <img :src="movie.Poster" :alt="movie.Title" class="rounded" />
          <span class="absolute bottom-5 right-0 text-white px-3 pb-1 capitalize font-bold" :class="[movie.Type == 'movie' ? 'bg-green-500' : 'bg-blue-500']">{{ movie.Type }}</span>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  props: {
    movie: Object,
  },
};
</script>

<style>
.image-container {
  width: fit-content;
}
</style>