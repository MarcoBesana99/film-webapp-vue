<template>
  <div>
    <nav-bar></nav-bar>
    <featured-card></featured-card>
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/NavBar'
import FeaturedCard from '@/components/FeaturedCard'

export default {
  name: 'Home',
  components: {
    NavBar,
    FeaturedCard
  }
}
</script>
