<template>
  <div>
    <nav-bar></nav-bar>
    <div v-if="!loading" class="flex justify-center items-center h-screen">
      <pacman-loader></pacman-loader>
    </div>
    <div v-if="loading" class="p-5">
        <h2><span class="font-bold text-3xl text-white mr-3">{{ movie.Title }}</span><span>({{ movie.Released }})</span></h2>
      <p class="mt-6 text-white lg:w-3/5">{{ movie.Plot }}</p>
      <img :src="movie.Poster" :alt="movie.Title" class="rounded mt-6">
      <div>
        <h3 class="font-semibold mt-6 text-white text-3xl">Info</h3>
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Duration</h4>
            <span class="mt-4 text-white">{{ movie.Runtime }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Type</h4>
            <span class="mt-4 text-white">{{ movie.Genre }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Director</h4>
            <span class="mt-4 text-white">{{ movie.Director }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Writer</h4>
            <span class="mt-4 text-white">{{ movie.Writer }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Actors</h4>
            <span class="mt-4 text-white">{{ movie.Actors }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Language</h4>
            <span class="mt-4 text-white">{{ movie.Language }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Country</h4>
            <span class="mt-4 text-white">{{ movie.Country }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Awards</h4>
            <span class="mt-4 text-white">{{ movie.Awards }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">BoxOffice</h4>
            <span class="mt-4 text-white">{{ movie.BoxOffice }}</span>
          </div>
          <div>
            <h4 class="text-white text-lg font-semibold mt-6">Production</h4>
            <span class="mt-4 text-white">{{ movie.Production }}</span>
          </div>
        </div>
        <div>
          <h3 class="font-semibold mt-6 text-white text-xl">Ratings</h3>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
            <div v-for="(rating, index) in movie.Ratings" :key="index">
            <h4 class="text-white text-lg font-semibold mt-4">{{ rating.Source }}</h4>
            <span class="mt-4 text-white">{{ rating.Value }}</span>
          </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import env from "@/env.js";
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import NavBar from "@/components/NavBar";
import PacmanLoader from 'vue-spinner/src/PacmanLoader.vue'

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();
    const loading = ref(false)
    onBeforeMount(() => {
      fetch(
        `http://www.omdbapi.com/?apikey=${env.apiKey}&i=${route.params.id}&plot=full`
      )
        .then((res) => res.json())
        .then((data) => {
          setTimeout(()=> {
            loading.value = true
          }, 2000)
          movie.value = data;
        });
    });

    return { movie, loading };
  },
  components: { NavBar, PacmanLoader },
};
</script>