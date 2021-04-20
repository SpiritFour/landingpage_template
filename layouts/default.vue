<template>
  <v-app class="gradientBG textColor">
    <Utils-Navbar />
    <v-main>
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
.gradientBG {
  background: linear-gradient(to bottom, #7927b2, #fb3182) !important;
}
.textColor {
  color: white !important;
}
</style>
