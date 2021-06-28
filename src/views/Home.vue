<template>
  <div>
    <nav-bar></nav-bar>
    <featured-card></featured-card>
    <movies-handler></movies-handler>
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from "@/components/NavBar";
import FeaturedCard from "@/components/FeaturedCard";
import MoviesHandler from "@/components/MoviesHandler";

export default {
  name: "Home",
  components: {
    NavBar,
    FeaturedCard,
    MoviesHandler
  },
};
</script>
