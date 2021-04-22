<template>
  <div data-aos-delay="50" :data-aos="feature.slide">
    <img
      class="icon"
      :src="require('~/assets/img/feature_images/' + feature.img)"
    />
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
