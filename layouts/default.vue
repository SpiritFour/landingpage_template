<i18n global>
{
  "en": {
    "title": "Title of Landingpage",
    "name": "rando"
  },
  "de": {
    "title": "Titel der Landingpage"
  }
}
</i18n>

<i18n>
{
  "en": {
    "login": "Login",
    "try": "Try"
  },
  "de": {
    "login": "Login",
    "try": "Probiere"
  }
}
</i18n>

<template>
  <v-app dark>
    <v-app-bar fixed app>
      <img src="~/assets/img/logo.png" height="100%" class="mr-4" />
      <v-toolbar-title>{{ $t('title') }}</v-toolbar-title>
      <v-spacer />
      <v-btn>
        {{ $t('login') }}
      </v-btn>
      <v-btn> {{ $t('try') }} {{ $t('name') }} </v-btn>
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
export default {}
</script>
