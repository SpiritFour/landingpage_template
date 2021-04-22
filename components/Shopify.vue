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
          <FreeTrialBtn />
        </v-col>
      </v-row>
    </v-col>
    <v-row class="text-caption mt-4 mx-auto" style="max-width: 400px">
      {{ $t('disclaimer') }}
    </v-row>
    <!--    focus feature-->
    <v-container class="mt-12" data-aos="fade-left" data-aos-delay="50">
      <v-row>
        <div class="text-h5 font-weight-black">
          Automatic out-of-focus Detection
        </div>
      </v-row>
      <v-row class="mt-8">
        <v-col justify="top" cols="12" sm="6">
          <img
            src="https://picsum.photos/seed/alksdjflöa/1600/1200"
            style="width: 80%"
          />
        </v-col>
        <v-col class="text-left"> <FeatureText :feature="$t('focus')" /></v-col>
      </v-row>
    </v-container>
    <!--    automatic sorting-->
    <v-container class="mt-12" data-aos="fade-right" data-aos-delay="50">
      <v-row>
        <div class="text-h5 font-weight-black">
          Automatic contentwise sorting
        </div>
      </v-row>
      <v-row>
        <transition-group name="flip-list" class="mt-8">
          <img
            v-for="img in imageSortingList"
            :key="img"
            :src="img"
            style="width: 30%; margin: 1.5%"
          />
        </transition-group>
      </v-row>
      <v-row class="text-left">
        <v-col>
          <FeatureText :feature="$t('sorting')" />
        </v-col>
      </v-row>
    </v-container>
    <v-container class="mt-12" data-aos="fade-left" data-aos-delay="50">
      <v-row>
        <div class="text-h5 font-weight-black">Instantaneous 100% preview</div>
      </v-row>
      <v-row justify="center" class="mt-8">
        <video ref="video" width="80%" autoplay preload="auto" muted loop>
          <source src="~/assets/video/video-full.webm" type="video/webm" />
          Your browser does not support video.
        </video>
      </v-row>
      <v-row class="text-left">
        <v-col>
          <FeatureText :feature="$t('instant')" />
        </v-col>
      </v-row>
    </v-container>
    <v-container class="mt-12">
      <v-row>
        <v-col v-for="i in 3" :key="i" cols="12" sm="4" class="text-left">
          <FeatureText :feature="$t('feature' + i)" />
        </v-col>
      </v-row>
    </v-container>
    <v-container class="mt-16" data-aos="fade-up" data-aos-delay="50">
      <v-row class="text-h5">
        {{ $t('testimonial.quote') }}
      </v-row>
      <v-row justify="center" class="text-body-2 font-weight-black mt-10">
        {{ $t('testimonial.from') }}
      </v-row>
      <v-row justify="center" class="mt-16"><FreeTrialBtn /></v-row>
    </v-container>
  </v-container>
</template>

<script>
import FeatureText from '~/components/FeatureText'
import FreeTrialBtn from '~/components/FreeTrialBtn'

export default {
  name: 'Shopify',
  components: { FreeTrialBtn, FeatureText },
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
      imageSortingList: [
        'https://picsum.photos/seed/alkssdffddfdjflöa/1600/1200',
        'https://picsum.photos/seed/alksasdsfdjflöa/1600/1200',
        'https://picsum.photos/seed/alksdasdfjflöa/1600/1200',
      ],
    }
  },
  methods: {
    shuffle() {
      this.imageSortingList.reverse()
    },
  },
  mounted() {
    this.shuffle()
    setInterval(this.shuffle, 3000)
  },
}
</script>

<style scoped>
.flip-list-move {
  transition: transform 1s;
}
</style>

<i18n lang="json5">
{
  en: {
    titlePhrase: 'Sell online with Shopify',
    subPhrase: 'Trusted by over 1,000,000 businesses worldwide',
    nameRequired: 'Name is required',
    nameLess10: 'Name must be less than 10 characters',
    emailRequired: 'E-mail is required',
    emailValid: 'E-mail must be valid',
    enterEmail: 'Enter your email address',
    disclaimer: 'Try Shopify free for 14 days, no credit card required. By entering your email, you agree to receive marketing emails from Shopify.',
    // focus overlay
    focus: {
      title: 'Detect out of focus regions easily',
      text: 'Bli bla blub this is really nice and you really need this',
      img: '1.svg',
    },
    // sorting feature
    sorting: {
      title: 'Automatically sorts your images contentwise',
      text: 'Bli bla blub this is really nice and you really need this',
      img: '1.svg',
    },
    // instant 100% feature
    instant: {
      title: 'Instantaneous 100% preview of your uncompressed raw images',
      text: 'Bli bla blub this is really nice and you really need this',
      img: '1.svg',
    },
    // Feature row
    feature1: {
      title: 'Beautiful themes that are responsive and customizable',
      text: 'No design skills needed. You have complete control over the look and feel of your website, from its layout, to content and colors.',
      img: '1.svg',
      slide: 'fade-up-right',
    },
    feature2: {
      title: 'Pricing as low as $29/month',
      text: 'Whether you sell online, on social media, in store, or out of the trunk of your car, Shopify has you covered. Start selling anywhere for just $29/month.',
      img: '2.svg',
      slide: 'fade-up',
    },
    feature3: {
      title: 'Trusted by over 1,000,000 businesses worldwide',
      text: 'Shopify handles everything from marketing and payments, to secure checkout and shipping',
      img: '3.svg',
      slide: 'fade-up-left',
    },
    testimonial: {
      quote: '“Shopify is better than any other platform we’ve played with, and we’ve played with them all.”',
      from: 'JONATHON BAYME, CEO OF THEORY11',
    },
  },
  de: {},
}
</i18n>
