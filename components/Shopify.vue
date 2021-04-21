<template>
  <v-container class="text-center textColor" style="max-width: 700px">
    <div class="text-h2 font-weight-bold mt-5">
      {{ $t('titlePhrase') }}
    </div>
    <div class="text-h4 mt-5">
      {{ $t('subPhrase') }}
    </div>
    <v-col class="mx-auto mt-4" style="max-width: 500px">
      <v-row justify="center" align="center">
        <v-col cols="12" sm="6" align="center">
          <v-text-field
            v-model="email"
            :rules="emailRules"
            :label="$t('enterEmail')"
            required
            style="max-width: 250px"
          >
          </v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-btn
            color="info"
            elevation="0"
            x-large
            class="font-weight-black"
            style="border-radius: 4px"
            >{{ $t('startFree') }}</v-btn
          >
        </v-col>
      </v-row>
    </v-col>
    <div class="text-caption mt-4 mx-auto" style="max-width: 400px">
      {{ $t('disclaimer') }}
    </div>
    <img
      data-aos="fade-right"
      data-aos-delay="50"
      src="~assets/img/product.png"
      style="width: 100%"
      class="mt-10"
    />
    <v-row class="mt-5">
      <v-col
        v-for="i in 3"
        :key="i"
        cols="12"
        sm="4"
        class="text-left"
        data-aos-delay="50"
        :data-aos="$t('slide' + i)"
      >
        <div class="icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 45 45">
            <path id="path-1" :d="$t('svg' + i)"></path>
          </svg>
        </div>

        <div class="text-subtitle-2 font-weight-bold">
          {{ $t('title' + i) }}
        </div>
        <div class="text-body-1 mt-4">{{ $t('text' + i) }}</div></v-col
      >
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Shopify',
  data() {
    return {
      valid: false,
      firstname: '',
      lastname: '',
      nameRules: [
        (v) => !!v || this.$t('nameRequired'),
        (v) => v.length <= 10 || this.$t('nameLess10'),
      ],
      email: '',
      emailRules: [
        (v) => !!v || this.$t('emailRequired'),
        (v) => /.+@.+/.test(v) || this.$t('emailValid'),
      ],
    }
  },
}
</script>

<style scoped>
.icon {
  width: 3em;
  fill: whitesmoke;
}
</style>

<i18n json5>
{
  "en": { "titlePhrase": "Sell online with Shopify",
    "subPhrase": "Trusted by over 1,000,000 businesses worldwide",
    "nameRequired": "Name is required",
    "nameLess10": "Name must be less than 10 characters",
    "emailRequired": "E-mail is required",
    "emailValid": "E-mail must be valid",
    "startFree": "Start free trial",
    "enterEmail": "Enter your email address",
    "disclaimer": "Try Shopify free for 14 days, no credit card required. By entering your email, you agree to receive marketing emails from Shopify.",
    "title1": "Beautiful themes that are responsive and customizable",
    "text1": "No design skills needed. You have complete control over the look and feel of your website, from its layout, to content and colors.",
    "svg1": "M34.5 36h-1a1.5 1.5 0 110-3h1a1.5 1.5 0 110 3zM38 9V7H7v23h8.829a1 1 0 011 1v1H21a1 1 0 011 1v1a1 1 0 01-1 1h-4.171A3.001 3.001 0 0114 33H5v4.5A1.5 1.5 0 006.5 39H21a1 1 0 011 1v1a1 1 0 01-1 1H6.5C4.02 42 2 39.99 2 38v-6c0-1.32.67-2 1.5-2H4V5.5A1.5 1.5 0 015.5 4h34A1.5 1.5 0 0141 5.5V9a1 1 0 01-1 1h-1a1 1 0 01-1-1zM28 39h12V16H28v23zm12.5 3h-13a2.503 2.503 0 01-2.5-2.5v-24c0-1.378 1.122-2.5 2.5-2.5h13c1.378 0 2.5 1.122 2.5 2.5v24c0 1.378-1.122 2.5-2.5 2.5z",
    "slide1": "fade-up-right",
    "title2": "Pricing as low as $29/month",
    "text2": "Whether you sell online, on social media, in store, or out of the trunk of your car, Shopify has you covered. Start selling anywhere for just $29/month.",
    "svg2": "M41 8H4a2 2 0 00-2 2v25a2 2 0 002 2h37a2 2 0 002-2V10a2 2 0 00-2-2zm-1 26H5V11h35zm-17-5c2.76 0 5-2.91 5-6.5S25.76 16 23 16s-5 2.91-5 6.5 2.24 6.5 5 6.5zm0-10c.92 0 2 1.53 2 3.5S23.92 26 23 26s-2-1.53-2-3.5 1.08-3.5 2-3.5zM7 15v-1a1 1 0 011-1h3a1 1 0 011 1v1a1 1 0 01-1 1H8a1 1 0 01-1-1zm26 16v-1a1 1 0 011-1h3a1 1 0 011 1v1a1 1 0 01-1 1h-3a1 1 0 01-1-1z",
    "slide2": "fade-up",
    "title3": "Trusted by over 1,000,000 businesses worldwide",
    "text3": "Shopify handles everything from marketing and payments, to secure checkout and shipping",
    "svg3": "M12.5 21A6.5 6.5 0 106 14.5a6.5 6.5 0 006.5 6.5zm0-10A3.5 3.5 0 119 14.5a3.5 3.5 0 013.5-3.5zM30 21a8 8 0 10-8-8 8 8 0 008 8zm0-13a5 5 0 11-5 5 5 5 0 015-5zm13 25.5v4a1.5 1.5 0 01-3 0v-4c0-3.77-2.52-6.5-6-6.5h-7.5a6.51 6.51 0 00-6.5 6.5v4a1.5 1.5 0 01-3 0v-4a9.51 9.51 0 019.5-9.5H34c5.13 0 9 4.08 9 9.5zm-27-8a1.5 1.5 0 01-1.5 1.5h-4A5.51 5.51 0 005 32.5V36a1.5 1.5 0 01-3 0v-3.5a8.51 8.51 0 018.5-8.5h4a1.5 1.5 0 011.5 1.5z",
    "slide3": "fade-up-left"
  },
  "de": {
  }
}
</i18n>
