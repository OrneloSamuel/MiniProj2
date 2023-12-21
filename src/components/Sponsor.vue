<template>
  <b-col cols="12" md="4" class="mb-3">
    <b-card
      :title="sponsor.name"
      :img-src="sponsor.photo_one"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem;"
      class="mb-5 h-100"
    >
      <b-card-text>{{ sponsor.description }}</b-card-text>
      <template #footer>
        <router-link
          :to="{ name: 'sponsor', params: { sponsorId: sponsor._id } }"
          tag="b-button"
          variant="outline-success"
        >
          <i class="fas fa-search"></i> Ver Mais
        </router-link>
      </template>
    </b-card>
  </b-col>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "Sponsor",
  props: ["sponsor"],
  methods: {
    ...mapGetters("auth", ["getProfile"])
  }
};
</script>
