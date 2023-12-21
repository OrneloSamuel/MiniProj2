<template>
  <section class="page-section">
    <b-container>
      <HeaderPage :title="expert.name" />
      <b-card class="overflow-hidden" style="max-width: 1540px;">
        <b-row cols="1" cols-sm="1" cols-md="2">
          <b-col cols="12" md="6" class="mb-3">
            <b-carousel
              id="carousel-fade"
              controls
              indicators
              background="#ababab"
              style="text-shadow: 1px 1px 2px #333"
              img-width="1024"
              img-height="480"
            >
              <b-carousel-slide :img-src="expert.photo_one"></b-carousel-slide>
              <b-carousel-slide :img-src="expert.photo_two"></b-carousel-slide>
              <b-carousel-slide :img-src="expert.photo_three"></b-carousel-slide>
            </b-carousel>
          </b-col>

          <b-col cols="12" md="6" class="mb-3">
            <h3 class="ps-5">Descrição</h3>

            <p>{{ expert.description }}</p>
          </b-col>
        </b-row>

        <b-row>
          <h3 class="m-3">Especialistas</h3>

          <b-col cols="12" md="12">
            <p v-if="this.expert.animals.length < 1">
              <i>Nenhum animal adicionado</i>
            </p>

            <b-tabs pills card vertical v-else>
              <b-tab
                v-for="animal in this.expert.animals"
                :key="animal._id"
                :title="findAnimal(animal.animal)"
                ><b-card-text>{{ animal.description }}</b-card-text></b-tab
              >
            </b-tabs>
          </b-col>
        </b-row>

        <b-row align-h="start" cols="1" cols-sm="1" cols-md="2">
          <div class="col-lg-6 col-6 mt-5">
            <h3>Nossas Páginas</h3>

            <div class="row mt-4">
              <div class="col-3">
                <a :href="expert.facebook" target="_blank"
                  ><span class="fab fa-facebook fa-2x text-secondary"></span
                ></a>
              </div>
              <div class="col-3">
                <a :href="expert.instagram" target="_blank"
                  ><span class="fab fa-instagram fa-2x text-secondary"></span
                ></a>
              </div>
              <div class="col-3">
                <a :href="expert.twitter" target="_blank"
                  ><span class="fab fa-twitter fa-2x text-secondary"></span
                ></a>
              </div>
              <div class="col-3">
                <a :href="expert.linkedin" target="_blank"
                  ><span class="fab fa-linkedin fa-2x text-secondary"></span
                ></a>
              </div>
            </div>
          </div>
        </b-row>

        <div class="row col-12 mt-5">
          <div class="col-lg-12 col-12 text-center">
            <router-link
              :to="{ name: 'experts' }"
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
    </b-container>
  </section>
</template>

<script>
import HeaderPage from "@/components/HeaderPage.vue";
import { mapGetters } from "vuex";
import { FETCH_ANIMALS } from "@/store/animals/animal.constants";

export default {
  name: "Expert",
  components: {
    HeaderPage
  },
  data: function() {
    return {
      expert: "",
      animals: []
    };
  },
  computed: {
    ...mapGetters("expert", ["getExpertsById", "getMessage"]),
    ...mapGetters("animal", ["getAnimalsById", "getMessage"])
  },
  methods: {
    findAnimal(id) {
      const animal = this.getAnimalsById(id);
      return animal.name;
    },
    console: () => console
  },
  created() {
    this.expert = this.getExpertsById(this.$route.params.expertId);
    this.$store.dispatch(`animal/${FETCH_ANIMALS}`).then(
      () => {
        this.animals = this.getAnimals;
      },
      err => {
        this.$alert(`${err.message}`, "Erro", "error");
      }
    );
  }
};
</script>
