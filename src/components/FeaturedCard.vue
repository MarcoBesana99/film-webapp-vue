<template>
  <div>
    <router-link to="/movie/tt0078346" class="relative">
      <div class="hero relative text-white p-6">
        <div
          class="
            absolute
            bg-gray-700
            w-full
            h-full
            top-0
            left-0
            z-10
            opacity-60
          "
        ></div>
        <div class="z-20 relative flex flex-col justify-end h-full">
          <div class="text-4xl font-bold pb-4">Superman</div>
          <p class="font-semibold">
            Just before the destruction of the planet Krypton, scientist Jor-El
            sends his infant son Kal-El on a spaceship to Earth. Raised by
            kindly farmers Jonathan and Martha Kent, young Clark discovers the
            source of his superhuman powers and moves to Metropolis to fight
            evil. As Superman, he battles the villainous Lex Luthor, while, as
            novice reporter Clark Kent, he attempts to woo co-worker Lois Lane
          </p>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style scoped>
.hero {
  background-image: url("https://i.pinimg.com/originals/c9/b0/a9/c9b0a90fb5914f08cbef46e9d90ea4e8.jpg");
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  height: 70vh;
}
@media screen and (max-width: 997px) {
  .hero {
    height: 60vh;
  }
}
</style>