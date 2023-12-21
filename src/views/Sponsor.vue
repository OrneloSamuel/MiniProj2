<template>
  <section class="page-section">
    <b-container>
      <HeaderPage :title="sponsor.name" />
      <b-row>
        <b-card class="overflow-hidden" style="max-width: 1540px;">
          <div class="row row-cols-lg-2 row-cols-md-2 row-cols-1 gy-5">
            <div
              class="justify-content-around col-lg-6 col-xs-12 col-md-6 mb-3"
            >
              <img
                :src="sponsor.photo_one"
                class="d-block w-100"
                alt="Image 1"
              />
            </div>

            <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
              <h3 class="ps-5">Descrição</h3>

              <p>{{ sponsor.description }}</p>
            </div>

            <div
              class="justify-content-around col-lg-6 col-xs-12 col-md-6 mb-3"
            >
              <img
                :src="sponsor.photo_two"
                class="d-block w-100"
                alt="Image 1"
              />
            </div>

            <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
              <h3 class="ps-5">Motivação</h3>

              <p>{{ sponsor.motivation }}</p>
            </div>

            <div
              class="justify-content-around col-lg-6 col-xs-12 col-md-6 mb-3"
            >
              <img
                :src="sponsor.photo_three"
                class="d-block w-100"
                alt="Image 3"
              />
            </div>

            <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
              <h3 class="ps-5">Nossas Páginas</h3>

              <div class="mt-5 text-center">
                <div class="row">
                  <div class="col-3 col-xs-3 col-sm-3">
                    <a :href="sponsor.facebook" target="_blank"
                      ><span class="fab fa-facebook fa-2x text-secondary"></span
                    ></a>
                  </div>
                  <div class="col-3">
                    <a :href="sponsor.instagram" target="_blank"
                      ><span
                        class="fab fa-instagram fa-2x text-secondary"
                      ></span
                    ></a>
                  </div>
                  <div class="col-3">
                    <a :href="sponsor.twitter" target="_blank"
                      ><span class="fab fa-twitter fa-2x text-secondary"></span
                    ></a>
                  </div>
                  <div class="col-3">
                    <a :href="sponsor.linkedin" target="_blank"
                      ><span class="fab fa-linkedin fa-2x text-secondary"></span
                    ></a>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="row col-12 mt-5">
            <div class="text-center col-lg-12 col-12">
              <router-link
                :to="{ name: 'sponsors' }"
                tag="b-button"
                variant="outline-success"
                align="center"
                class="btn btn-secondary"
              >
                <i class="fas fa-arrow-circle-left"></i> VOLTAR
              </router-link>
            </div>
          </div>
        </b-card>
      </b-row>
    </b-container>
  </section>
</template>

<script>
import HeaderPage from "@/components/HeaderPage.vue";
import { mapGetters } from "vuex";

export default {
  name: "sponsor",
  components: {
    HeaderPage
  },
  data: function() {
    return {
      sponsor: ""
    };
  },
  computed: {
    ...mapGetters("sponsor", ["getSponsorsById", "getMessage"])
  },
  created() {
    this.sponsor = this.getSponsorsById(this.$route.params.sponsorId);
  }
};
</script>
