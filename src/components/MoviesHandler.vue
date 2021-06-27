<template>
  <div>
    <form @submit.prevent="SearchMovies()" class="flex justify-center mt-7">
      <input
        type="text"
        placeholder="Search your movie"
        v-model="search"
        class="rounded p-1 mr-4 w-2/5"
      />
      <input
        type="submit"
        value="Search"
        class="
          cursor-pointer
          px-3
          py-1
          rounded
          bg-green-500
          hover:bg-green-700
          text-white
          font-semibold
          transition-colors
          duration-100
          ease-in-out
        "
      />
    </form>
    <div v-if="error != ''" class="flex justify-center mt-4">
      <span class="text-center bg-red-500 text-white font-semibold px-3 pb-1">{{
        error
      }}</span>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 p-5 gap-5">
      <div
        v-for="movie in movies"
        :key="movie.imdbID"
        class="flex justify-center"
      >
        <movie-card :movie="movie"></movie-card>
      </div>
    </div>
  </div>
</template>

<script>
import env from "@/env.js";
import { ref } from "vue";
import MovieCard from "@/components/MovieCard";
export default {
  setup() {
    const search = ref("");
    const error = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?apikey=${env.apiKey}&s=${search.value}`)
          .then((res) => res.json())
          .then((data) => {
            if (data.Response == "True") {
              error.value = "";
              movies.value = data.Search.filter(
                (movie) => movie.Poster != "N/A"
              );
            } else {
              error.value = data.Error;
              movies.value = [];
            }
            search.value = "";
          });
      }
    };

    return { search, movies, SearchMovies, error };
  },
  components: {
    MovieCard,
  },
};
</script>