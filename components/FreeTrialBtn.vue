<template>
  <v-row justify="center" align="center">
    <v-col v-if="!jump" cols="12" sm="6" align="center">
      <v-form
        action="https://buttondown.email/api/emails/embed-subscribe/ReimaginingImageCulling"
        method="post"
        target="popupwindow"
        id="form"
        ref="form"
      >
        <v-text-field
          name="email"
          v-model="email"
          :rules="emailRules"
          :label="$t('enterEmail')"
          required
          style="max-width: 250px"
        >
        </v-text-field>
      </v-form>
    </v-col>
    <v-col cols="12" sm="6">
      <v-btn
        action="https://buttondown.email/api/emails/embed-subscribe/ReimaginingImageCulling"
        method="post"
        target="popupwindow"
        color="info"
        elevation="0"
        x-large
        class="font-weight-black"
        style="border-radius: 4px"
        @click="click"
        >{{ $t('startFree') }}
      </v-btn>
    </v-col>
  </v-row>
</template>
<script>
export default {
  name: 'FreeTrialBtn',
  props: {
    jump: false,
  },
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
  methods: {
    click() {
      if (this.jump) {
        this.$vuetify.goTo(0, { duration: 300, offset: 100 })
      } else {
        if (this.$refs.form.validate()) {
          form.submit()
        }
      }
    },
  },
}
</script>

<i18n lang="json5">
{
  en: {
    startFree: 'Start free trial',
    emailRequired: 'E-mail is required',
    emailValid: 'E-mail must be valid',
    enterEmail: 'Enter your email address',
  },
}
</i18n>
