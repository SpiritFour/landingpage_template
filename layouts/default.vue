<template>
  <v-app class="transparentBG">
    <Utils-Navbar />
    <v-main class="animatedBG" style="overflow: hidden">
      <nuxt />
    </v-main>
    <v-footer absolute color="transparent" padless app>
      <v-col class="text-center" cols="12">
        <span>&copy; {{ new Date().getFullYear() }}</span>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {}
</script>

<style>
.transparentBG {
  background: rgba(0, 0, 0, 0) !important;
}
.gradientBG2 {
  background: linear-gradient(to bottom, #7927b2, #fb3182) !important;
}
.animatedBG {
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 15s ease infinite;
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
</style>
