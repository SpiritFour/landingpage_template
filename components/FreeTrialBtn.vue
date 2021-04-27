<template>
  <v-row justify="center" align="center">
    <v-col v-if="!jump" cols="12" sm="6" align="center">
      <v-row justify="center">
        <v-col
          align-self="center"
          cols="auto"
          class="mx-0 pa-0"
          style="background: white"
          ><div class="transparentFont animatedBG font-weight-black">
            Then
          </div></v-col
        >
        <v-col style="max-width: 220px">
          <v-form
            action="https://buttondown.email/api/emails/embed-subscribe/ReimaginingImageCulling"
            method="post"
            target="popupwindow"
            id="form"
            ref="form"
          >
            <v-text-field
              id="emailField"
              name="email"
              v-model="email"
              :rules="emailRules"
              :label="$t('enterEmail')"
              required
              solo
              background-color="white"
              light
            >
            </v-text-field>
          </v-form>
        </v-col>
      </v-row>
    </v-col>
    <v-col cols="12" sm="6">
      <v-row justify="center">
        <v-col
          v-if="!jump"
          align-self="center"
          cols="auto"
          class="mx-0 pa-0"
          style="background: white"
          ><div class="transparentFont animatedBG font-weight-black">
            and
          </div></v-col
        >
        <v-col style="max-width: 220px">
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

<style>
.transparentFont {
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
.label {
  font-size: 0.85em;
}
</style>

<i18n lang="json5">
{
  en: {
    startFree: 'Start free trial',
    emailRequired: 'E-mail is required',
    emailValid: 'E-mail must be valid',
    enterEmail: 'Email',
  },
}
</i18n>
