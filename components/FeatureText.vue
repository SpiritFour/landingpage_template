<template>
  <div data-aos-delay="50" :data-aos="feature.slide">
    <v-icon size="42">{{ feature.img }}</v-icon>
    <div class="text-subtitle-2 font-weight-bold">
      {{ feature.title }}
    </div>
    <div class="text-body-1 mt-4">{{ feature.text }}</div>
  </div>
</template>
<script>
export default {
  name: 'FeatureText',
  props: {
    feature: {},
  },
}
</script>
<style scoped>
.icon {
  width: 3em;
  filter: invert();
  -webkit-filter: invert();
}
</style>
