<template>
  <v-btn
    color="info"
    elevation="0"
    x-large
    class="font-weight-black"
    style="border-radius: 4px"
    >{{ $t('startFree') }}
  </v-btn>
</template>
<script>
export default {
  name: 'FreeTrialBtn',
}
</script>

<i18n lang="json5">
{
  en: {
    startFree: 'Start free trial',
  },
}
</i18n>
