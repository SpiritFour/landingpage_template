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
      data-aos="slide-right"
      data-aos-delay="50"
      data-aos-offset="400"
      src="~assets/img/product.png"
      style="width: 100%"
      class="mt-10"
    />
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
    "disclaimer": "Try Shopify free for 14 days, no credit card required. By entering your email, you agree to receive marketing emails from Shopify."
  },
  "de": {
  }
}
</i18n>
