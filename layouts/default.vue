<i18n>
{
  "en": {
    "login": "Login",
    "startFreeTrial": "Start free Trial"
  },
  "de": {
    "login": "Login",
    "startFreeTrial": "Kostenloser Probezugang"
  }
}
</i18n>

<template>
  <v-app dark>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn @click.stop="rightDrawer = !rightDrawer">
        {{ $t('login') }}
      </v-btn>
      <v-btn @click.stop="rightDrawer = !rightDrawer">
        {{ $t('startFreeTrial') }}
      </v-btn>
      <Utils-LanguageSwitcher />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
    }
  },
}
</script>
