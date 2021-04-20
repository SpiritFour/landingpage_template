<template>
  <v-app dark>
    <Utils-Navbar />
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
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
