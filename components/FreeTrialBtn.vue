<template>
  <v-row justify="center" align="center">
    <v-col v-if="!jump" cols="12" sm="8">
      <v-form
        action="https://buttondown.email/api/emails/embed-subscribe/ReimaginingImageCulling"
        method="post"
        target="popupwindow"
        id="form"
        ref="form"
      >
        <v-text-field
          class="input-padding"
          name="email"
          :label="$t('enterEmail')"
          :rules="emailRules"
          required
          solo
          background-color="white"
          light
          style="width: 100%"
        >
        </v-text-field>
      </v-form>
    </v-col>
    <v-col cols="12" sm="4" class="mt-0 pb-10">
      <v-btn
        action="https://buttondown.email/api/emails/embed-subscribe/ReimaginingImageCulling"
        method="post"
        target="popupwindow"
        color="info"
        elevation="0"
        x-large
        class="font-weight-black"
        style="border-radius: 4px"
        :style="
          $vuetify.breakpoint.smAndUp ? '' : 'width: 100%; margin-top: -30px '
        "
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

<style>
.input-padding div div div * {
  padding-left: 10px;
}
</style>
<i18n lang="json5">
{
  en: {
    startFree: 'Start free trial',
    emailRequired: '⚠️ E-mail is required',
    emailValid: '⚠️ E-mail must be valid',
    enterEmail: 'Enter your email address',
  },
}
</i18n>
