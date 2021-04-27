<template>
  <v-container class="text-center textColor" style="max-width: 700px">
    <div class="text-h2 font-weight-bold mt-5">
      {{ $t('titlePhrase') }}
    </div>
    <div class="text-h4 mt-5">
      {{ $t('subPhrase') }}
    </div>
    <v-col class="mx-auto mt-4" style="max-width: 900px">
      <FreeTrialBtn />
    </v-col>
    <v-row class="text-caption mt-4 mx-auto" style="max-width: 600px">
      {{ $t('disclaimer') }}
    </v-row>
    <v-container class="mt-12">
      <v-row>
        <v-col v-for="i in 3" :key="i" cols="12" sm="4" class="text-left">
          <FeatureText :feature="$t('feature' + i)" />
        </v-col>
      </v-row>
    </v-container>
    <v-container class="mt-4" data-aos="fade-right" data-aos-delay="50">
      <v-row class="text-h5 font-weight-black" justify="center" id="Sorting">
        {{ $t('sorting.heading') }}
      </v-row>
      <v-row justify="center">
        {{
          $t(
            this.sortedByTime ? 'sorting.timeSorted' : 'sorting.categorySorted'
          )
        }}
      </v-row>
      <transition-group name="flip-list" class="mt-8 row">
        <v-col v-for="data in imageSortingList" :key="data.img">
          <img
            :src="data.img"
            :style="'width: ' + ($vuetify.breakpoint.smAndUp ? 110 : 90) + 'px'"
          />
          <div class="text-caption text-center grey--text text--lighten-2">
            {{ data.date.toLocaleTimeString() }}
          </div>
        </v-col>
      </transition-group>
      <v-row class="text-left">
        <v-col>
          <FeatureText :feature="$t('sorting')" />
        </v-col>
      </v-row>
    </v-container>
    <!--    instant 100% -->
    <v-container class="mt-12" data-aos="fade-left" data-aos-delay="50">
      <v-row class="text-h5 font-weight-black" justify="center" id="Preview">
        {{ $t('instant.heading') }}
      </v-row>
      <v-row justify="center" class="mt-8">
        <video
          ref="video"
          width="80%"
          height="100%"
          autoplay
          preload="auto"
          muted
          loop
          playsinline
        >
          <source src="~/assets/video/video-full.webm" type="video/webm" />
          <source src="~/assets/video/video-full.mp4" type="video/mp4" />
          Your browser does not support video.
        </video>
      </v-row>
      <v-row class="text-left">
        <v-col>
          <FeatureText :feature="$t('instant')" />
        </v-col>
      </v-row>
    </v-container>
    <v-container class="mt-12" data-aos="fade-left" data-aos-delay="50">
      <v-row class="text-h5 font-weight-black" justify="center" id="Focus">
        {{ $t('focus.heading') }}
      </v-row>
      <v-row class="mt-8">
        <v-col justify="top" cols="12" sm="6">
          <div style="position: relative; width: 80%; margin: auto">
            <img
              src="~/assets/img/features/focus_peaking/1.jpg"
              style="width: 100%"
            />
            <img
              data-aos="fade"
              data-aos-easing="ease-in-out"
              data-aos-duration="1000"
              data-aos-anchor-placement="center-center"
              src="~/assets/img/features/focus_peaking/2.jpg"
              style="width: 100%; position: absolute; left: 0; top: 0"
            />
          </div>
        </v-col>
        <v-col class="text-left"> <FeatureText :feature="$t('focus')" /></v-col>
      </v-row>
    </v-container>
    <!--    rando features-->
    <!--    <v-container class="mt-12">-->
    <!--      <v-row>-->
    <!--        <v-col v-for="i in 3" :key="i" cols="12" sm="4" class="text-left">-->
    <!--          <FeatureText :feature="$t('feature' + i)" />-->
    <!--        </v-col>-->
    <!--      </v-row>-->
    <!--    </v-container>-->
    <!--    testimonial images-->
    <!--    <v-container>-->
    <!--      <v-row>-->
    <!--        <v-col v-for="i in 8" :key="i * 10">-->
    <!--          <img-->
    <!--            :src="require(`~/assets/img/features/testimonials/${i}.png`)"-->
    <!--            style="width: 90px"-->
    <!--          />-->
    <!--        </v-col>-->
    <!--      </v-row>-->
    <!--    </v-container>-->
    <!--    testimonial and jump up-->
    <v-container class="mt-16" data-aos="fade-up" data-aos-delay="50">
      <v-row class="text-h5">
        {{ $t('testimonial.quote') }}
      </v-row>
      <v-row justify="center" class="text-body-2 font-weight-black mt-10">
        {{ $t('testimonial.from') }}
      </v-row>
      <v-row justify="center" class="mt-16"
        ><FreeTrialBtn :jump="true"
      /></v-row>
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
    var imageOrdering = [
      0,
      0.5,
      11,
      3,
      3,
      7,
      7,
      7,
      2,
      1,
      6,
      0,
      2,
      2,
      1,
      11,
      11,
      5,
      5,
      5,
      5,
    ]
    return {
      imageOrdering,
      imageSortingList: [...Array(15).keys()].map((i) => {
        return {
          img: require(`~/assets/img/features/sorting/sorting-${i + 1}.jpg`),
          date: new Date(i * 200000 + Math.random() * 10000 + 30000000),
          randomOrder: i,
          actualOrder: imageOrdering[i],
        }
      }),
      showFocus: false,
      sortedByTime: true,
    }
  },
  methods: {
    shuffle() {
      this.imageSortingList.sort((a, b) => a.actualOrder - b.actualOrder)
      this.sortedByTime = false
      setTimeout(() => {
        this.imageSortingList.sort((a, b) => a.randomOrder - b.randomOrder)
        this.sortedByTime = true
      }, 5000)
    },
  },
  mounted() {
    this.shuffle()
    setInterval(this.shuffle, 10000)
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
    titlePhrase: 'Lightning fast Image Culling Application',
    subPhrase: 'Do you want to spend less time pre-selecting your images?',
    nameRequired: 'Name is required',
    nameLess10: 'Name must be less than 10 characters',
    disclaimer: 'Sign up for free so we can keep you updated about new features and gather feedback. We want to build this product with you.',
    // focus overlay
    focus: {
      heading: 'Automatic Out-Of-Focus Detection',
      title: 'Detect out of focus regions easily',
      text: 'Finally you dont have to spent hours sifting through images were the object is out of focus. We have automized this process by grouping out of focus images automatically with our AI. You stay in control at all time and still choose at any step',
      img: 'mdi-image-filter-center-focus-strong',
    },
    // sorting feature
    sorting: {
      heading: 'Automatic content sorting',
      title: 'Automatically sorts your images by content',
      text: 'Ever wondered where this one shot went and you can not recall where you have placed it? Or lost complete oversight of your library. Our app groups your content by topic or person and creates a readable file archive. So you spent less time searching for the perfect shoot.',
      img: 'mdi-sort-variant',
      timeSorted: 'Sorted by Date',
      categorySorted: 'Sorted by Category',
    },
    // instant 100% feature
    instant: {
      heading: 'Lag free 100% preview',
      title: 'Directly get access tom a 100% preview of your uncompressed raw images',
      text: 'No stutter or lag when cycling through your images, they load instantly. You can directly zoom to the relevant parts to manually check the sharpness.',
      img: 'mdi-magnify-plus-outline',
    },
    // Feature row
    feature1: {
      title: 'AI enabled content sorting',
      img: 'mdi-sort-variant',
      slide: 'fade-up-right',
    },
    feature2: {
      title: 'Automatic Out-Of-Focus Detection',
      img: 'mdi-image-filter-center-focus-strong',
      slide: 'fade-up-right',
    },
    feature3: {
      title: 'Lag free 100% preview',
      img: 'mdi-magnify-plus-outline',
      slide: 'fade-up-right',
    },
    testimonial: {
      quote: '“PhotoPicker is better than any other Culling Application we’ve played with, and we’ve played with them all.”',
      from: 'Moritz Wolf, CEO OF WhatsAnalyze',
    },
  },
  de: {
    titlePhrase: 'Blitzschnelle Foto sortier Anwendung',
    subPhrase: 'Wollen Sie weniger Zeit mit der Vorauswahl Ihrer Bilder verbringen?',
    nameRequired: 'Name ist erforderlich',
    nameLess10: 'Name muss weniger als 10 Zeichen lang sein',
    disclaimer: 'Testen Sie PhotoPicker kostenlos für 14 Tage, keine Kreditkarte erforderlich. Durch die Eingabe Ihrer E-Mail stimmen Sie zu, Marketing-E-Mails von PhotoPicker zu erhalten.',
    // Fokus-Overlay
    focus: {
      Überschrift: 'Automatische Unschärfe-Erkennung',
      title: 'Unscharfe Bereiche einfach erkennen',
      text: 'Endlich müssen Sie sich nicht mehr durch Bilder wühlen, in denen das Objekt unscharf ist. Wir haben diesen Prozess automatisiert, indem wir unscharfe Bilder durch KI gruppieren. Sie behalten jederzeit die Kontrolle und können immer noch in jedem Schritt wählen',
      img: 'mdi-image-filter-center-focus-strong',
    },
    // Sortierfunktion
    Sortierung: {
      Überschrift: 'Automatische Inhaltssortierung',
      title: 'Sortiert Ihre Bilder automatisch nach Inhalt',
      text: 'Haben Sie sich schon einmal gefragt, wo diese eine Aufnahme geblieben ist und Sie können sich nicht erinnern, wo Sie sie platziert haben? Unsere App gruppiert Ihre Inhalte nach Thema oder Person und erstellt ein übersichtliches Dateiarchiv. So verbringen Sie weniger Zeit mit der Suche nach der perfekten Aufnahme.',
      img: 'mdi-sort-variant',
      timeSorted: 'Sorted by Date',
      categorySorted: 'Sortiert nach Kategorie',
    },
    // sofortige 100%-Funktion
    instant: {
      Überschrift: 'Sofortige 100%-Vorschau ohne Verzögerung',
      title: 'Sofortiger Zugriff auf eine 100%-Vorschau Ihrer unkomprimierten Rohbilder',
      text: 'Kein Stottern oder Lag beim Durchblättern Ihrer Bilder, sie werden sofort geladen. Sie können direkt auf die relevanten Teile zoomen, um die Schärfe manuell zu überprüfen.',
      img: 'mdi-magnify-plus-outline',
    },
  },
}
</i18n>
