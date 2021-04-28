<template>
  <div>
    <!--    this is for all sm and up devices-->
    <v-app-bar absolute app elevation="0" style="background: transparent">
      <span class="font-weight-black text-h5">
        <v-icon class="font-weight-black">mdi-eyedropper-variant</v-icon
        >{{ $t('name') }}.app
      </span>

      <div
        v-if="$vuetify.breakpoint.mdAndUp"
        v-for="entry in content"
        :key="entry.name"
      >
        <v-btn elevation="0" plain class="pt-2" @click="clickHandler(entry.id)">
          {{ entry.name }}
        </v-btn>
      </div>

      <v-spacer />
      <v-app-bar-nav-icon
        v-if="$vuetify.breakpoint.smAndDown"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <Utils-LanguageSwitcher v-else />
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
        <v-list-item v-for="entry in content" :key="entry.name">
          <v-btn
            elevation="0"
            plain
            class="pt-2"
            @click="clickHandler(entry.id)"
          >
            {{ entry.name }}
          </v-btn>
        </v-list-item>
        <v-list-item> </v-list-item>
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
    return {
      drawer: false,
      content: [
        { name: 'Sorting', id: '#Sorting' },
        { name: 'Preview', id: '#Preview' },
        { name: 'Focus', id: '#Focus' },
      ],
    }
  },
  methods: {
    clickHandler(target) {
      this.$vuetify.goTo(target, { duration: 300, offset: 100 })
    },
  },
}
</script>

<style>
.white-image {
  filter: invert();
  -webkit-filter: invert();
}
</style>

<i18n global>
{
  "en": {
    "name": "Photopicker"
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
