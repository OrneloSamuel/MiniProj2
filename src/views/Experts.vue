<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Especialistas" />
      <Expert />
    </b-container>
  </section>
</template>

<script>
import Expert from "@/components/Expert.vue";
import HeaderPage from "@/components/HeaderPage.vue";
import { FETCH_EXPERTS } from "@/store/experts/expert.constants";

import { mapGetters } from "vuex";

export default {
  name: "Experts",
  components: {
    HeaderPage,
    Expert
  },
  data: function() {
    return {
      reverse: false,
      Experts: [],
      userLevel:0
    };
  },
  computed: {
    ...mapGetters(["getUserLevelByPoints"]),
    ...mapGetters('auth', ["getProfile"]),
    ...mapGetters("Expert", ["getExperts","getMessage"]),
    classSorter() {
      return {
        "fas fa-sort-alpha-up": !this.reverse,
        "fas fa-sort-alpha-down": this.reverse
      };
    }
  },
  methods: {
    compareExpertNames(Expert1, Expert2) {
      if (!this.reverse) {
        if (Expert1.name > Expert2.name) return 1;
        if (Expert1.name < Expert2.name) return -1;
      } else {
        if (Expert1.name < Expert2.name) return 1;
        if (Expert1.name > Expert2.name) return -1;
      }
      return 0;
    },
    sortExperts() {
      this.Experts.sort(this.compareExpertNames);
      this.reverse = !this.reverse;
    }
  },
  created() {
    this.$store
      .dispatch(`Expert/${FETCH_EXPERTS}`)
      .then(
        () => {
          this.Experts = this.getExperts.filter(
            Expert => Expert.level <= this.getUserLevelByPoints(this.getProfile.gamification.points).level
          )
        },
        err => this.$alert(`${err.message}`, "Erro", "error")
      );
  }
};
</script>
