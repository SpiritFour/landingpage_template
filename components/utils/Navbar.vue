<template>
  <div>
    <!--    this is for all sm and up devices-->
    <v-app-bar
      v-if="$vuetify.breakpoint.mdAndUp"
      fixed
      app
      elevation="0"
      color="transparent"
    >
      <img src="~/assets/img/logo.png" height="100%" class="mr-4" />
      <v-toolbar-title class="text-button font-weight-black">{{
        $t('name')
      }}</v-toolbar-title>

      <v-btn elevation="0" plain>
        {{ $t('features') }}
      </v-btn>
      <v-btn elevation="0" plain>
        {{ $t('pricing') }}
      </v-btn>
      <v-btn elevation="0" plain>
        {{ $t('ourMission') }}
      </v-btn>
      <v-spacer />
      <v-btn elevation="0" plain>
        {{ $t('login') }}
      </v-btn>
      <v-btn elevation="0" color="primary">
        {{ $t('try') }} {{ $t('name') }}
      </v-btn>
      <Utils-LanguageSwitcher />
    </v-app-bar>
    <!--    for smaller devices add drawer-->
    <v-app-bar v-else app absolute elevation="0" color="transparent">
      <img src="~/assets/img/logo.png" height="100%" class="mr-4" />
      <v-toolbar-title>{{ $t('name') }}</v-toolbar-title>
      <v-spacer></v-spacer>

      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
    </v-app-bar>
    <v-navigation-drawer
      v-model="drawer"
      app
      right
      temporary
      class="animatedBG"
    >
      <v-list nav dense class="d-flex justify-end align-center">
        <Utils-LanguageSwitcher class="pl-5" />
        <v-spacer></v-spacer>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      </v-list>
      <v-list nav dense>
        <v-list-item>
          <v-btn elevation="0" plain>
            {{ $t('features') }}
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn elevation="0" plain>
            {{ $t('pricing') }}
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn elevation="0" plain>
            {{ $t('ourMission') }}
          </v-btn>
        </v-list-item>
        <v-list-item> </v-list-item>
        <v-list-item>
          <v-btn elevation="0" plain>
            {{ $t('login') }}
          </v-btn>
        </v-list-item>
        <v-list-item>
          <v-btn elevation="0" color="primary">
            {{ $t('try') }} {{ $t('name') }}
          </v-btn>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  data() {
    return { drawer: false }
  },
}
</script>

<i18n global>
{
  "en": {
    "name": "rando"
  },
  "de": {
  }
}
</i18n>

<i18n>
{
  "en": {
    "login": "Login",
    "try": "Try",
    "ourMission": "Our Mission",
    "features": "Features",
    "pricing": "Pricing"
  },
  "de": {
    "login": "Login",
    "try": "Probiere",
    "ourMission": "Unsere Vision",
    "features": "Features",
    "pricing": "Preis"
  }
}
</i18n>
