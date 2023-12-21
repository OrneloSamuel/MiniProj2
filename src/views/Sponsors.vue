<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Patrocinadores" />
      <b-row align-h="center" cols="1" cols-sm="1" cols-md="3">
        <Sponsor
          v-for="sponsor in sponsors"
          :key="sponsor.id"
          :sponsor="sponsor"
        />
      </b-row>
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
      sponsors: []
    };
  },
  computed: {
    ...mapGetters("sponsor", ["getSponsors"])
  },
  methods: {
    fetchSponsors() {
      this.$store.dispatch(`sponsor/${FETCH_SPONSORS}`).then(
        () => {
          this.sponsors = this.getSponsors;
          this.sponsors.sort(this.compareLevels);
        },
        err => this.$alert(`${err.message}`, "Erro", "error")
      );
    },
    compareLevels(sponsor1, sponsor2) {
      if (sponsor1.name > sponsor2.name) return 1;
      if (sponsor1.name < sponsor2.name) return -1;
      else return 0;
    }
  },
  created() {
    this.fetchSponsors();
  }
};
</script>
