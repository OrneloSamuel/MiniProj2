<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Especialistas" />
      <b-row align-h="center" cols="1" cols-sm="1" cols-md="3">
        <Expert v-for="expert in experts" :key="expert.id" :expert="expert" />
      </b-row>
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
      experts: []
    };
  },
  computed: {
    ...mapGetters("expert", ["getExperts"])
  },
  methods: {
    fetchExperts() {
      this.$store.dispatch(`expert/${FETCH_EXPERTS}`).then(
        () => {
          this.experts = this.getExperts;
          this.experts.sort(this.compareLevels);
        },
        err => this.$alert(`${err.message}`, "Erro", "error")
      );
    },
    compareLevels(expert1, expert2) {
      if (expert1.name > expert2.name) return 1;
      if (expert1.name < expert2.name) return -1;
      else return 0;
    }
  },
  created() {
    this.fetchExperts();
  }
};
</script>
