<template>
  <div>
    <v-select
      v-model="selectedLocale"
      :items="availableLocales"
      style="width: min-content"
      eager
      flat
      dense
      filled
      hide-details
      rounded
    >
      <template #selection="{ item }">
        <img :src="item.flag" style="width: 2em" class="ml-2" />
      </template>
      <template #item="{ item }">
        <img :src="item.flag" style="width: 2em" class="mr-2" />
        {{ item.text }}
      </template>
    </v-select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      availableLocales: [
        {
          value: 'en',
          text: 'English',
          flag: `${require(`~/assets/img/locales/en.svg`)}`,
          iso: 'en-GB',
        },
        {
          value: 'de',
          text: 'Deutsch',
          flag: `${require(`~/assets/img/locales/de.svg`)}`,
          iso: 'de-DE',
        },
      ],
      selectedLocale: this.$i18n.locale,
    }
  },
  watch: {
    selectedLocale(newLocale) {
      this.$router.push(this.switchLocalePath(newLocale))
    },
  },
}
</script>

<style>
.v-input__append-inner {
  display: none !important;
}
.v-input__slot {
  background: transparent !important;
  padding: 0 !important;
}
</style>
