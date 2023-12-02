<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Patrocinadores" />
      <Sponsor />
    </b-container>
  </section>
</template>

<script>
import Sponsor from "@/components/Sponsor.vue";
import HeaderPage from "@/components/HeaderPage.vue";
import { FETCH_SPONSORS } from "@/store/sponsors/sponsor.constants";

import { mapGetters } from "vuex";

export default {
  name: "Sponsors",
  components: {
    HeaderPage,
    Sponsor
  },
  data: function() {
    return {
      reverse: false,
      sponsors: [],
      userLevel:0
    };
  },
  computed: {
    ...mapGetters(["getUserLevelByPoints"]),
    ...mapGetters('auth', ["getProfile"]),
    ...mapGetters("sponsor", ["geSponsors","getMessage"]),
    classSorter() {
      return {
        "fas fa-sort-alpha-up": !this.reverse,
        "fas fa-sort-alpha-down": this.reverse
      };
    }
  },
  methods: {
    compareSponsorNames(sponsor1, sponsor2) {
      if (!this.reverse) {
        if (sponsor1.name > sponsor2.name) return 1;
        if (sponsor1.name < sponsor2.name) return -1;
      } else {
        if (sponsor1.name < sponsor2.name) return 1;
        if (sponsor1.name > sponsor2.name) return -1;
      }
      return 0;
    },
    sorSponsors() {
      this.sponsors.sort(this.comparesponsorNames);
      this.reverse = !this.reverse;
    }
  },
  created() {
    this.$store
      .dispatch(`sponsor/${FETCH_SPONSORS}`)
      .then(
        () => {
          this.sponsors = this.geSponsors.filter(
            sponsor => sponsor.level <= this.getUserLevelByPoints(this.getProfile.gamification.points).level
          )
        },
        err => this.$alert(`${err.message}`, "Erro", "error")
      );
  }
};
</script>
