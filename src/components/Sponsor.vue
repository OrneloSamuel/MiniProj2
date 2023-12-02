<template>
  <b-row>
    <div class="row row-cols-lg-3 row-cols-md-3 row-cols-1 gy-4">
      <div class="justify-content-around col-lg-4 col-xs-12 col-md-6 mb-4">
        <div class="card">
          <img src="../assets/animalec.png" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">Patrocinador 1</h5>
            <p class="card-text">
              Descrição acerca do patrocinador. Descrição acerca do
              patrocinador. Descrição acerca do patrocinador. Descrição acerca
              do patrocinador. Descrição acerca do patrocinador.
            </p>
            <router-link
              :to="{ name: 'sponsor' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="mr-2"
            >
              <i class="fas fa-eye"></i> Ver Mais
            </router-link>
          </div>
        </div>
      </div>

      <div class="justify-content-around col-lg-4 col-xs-12 col-md-6 mb-4">
        <div class="card">
          <img src="../assets/animalec.png" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">Patrocinador 2</h5>
            <p class="card-text">
              Descrição acerca do patrocinador. Descrição acerca do
              patrocinador. Descrição acerca do patrocinador. Descrição acerca
              do patrocinador. Descrição acerca do patrocinador.
            </p>
            <router-link
              :to="{ name: 'sponsor' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="mr-2"
            >
              <i class="fas fa-eye"></i> Ver Mais
            </router-link>
          </div>
        </div>
      </div>

      <div class="justify-content-around col-lg-4 col-xs-12 col-md-6 mb-4">
        <div class="card">
          <img src="../assets/animalec.png" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">Patrocinador 3</h5>
            <p class="card-text">
              Descrição acerca do patrocinador. Descrição acerca do
              patrocinador. Descrição acerca do patrocinador. Descrição acerca
              do patrocinador. Descrição acerca do patrocinador.
            </p>
            <router-link
              :to="{ name: 'sponsor' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="mr-2"
            >
              <i class="fas fa-eye"></i> Ver Mais
            </router-link>
          </div>
        </div>
      </div>

      <div class="justify-content-around col-lg-4 col-xs-12 col-md-6 mb-4">
        <div class="card">
          <img src="../assets/animalec.png" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">Patrocinador 4</h5>
            <p class="card-text">
              Descrição acerca do patrocinador. Descrição acerca do
              patrocinador. Descrição acerca do patrocinador. Descrição acerca
              do patrocinador. Descrição acerca do patrocinador.
            </p>
            <router-link
              :to="{ name: 'sponsor' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="mr-2"
            >
              <i class="fas fa-eye"></i> Ver Mais
            </router-link>
          </div>
        </div>
      </div>

      <div class="justify-content-around col-lg-4 col-xs-12 col-md-6 mb-4">
        <div class="card">
          <img src="../assets/animalec.png" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">Patrocinador 5</h5>
            <p class="card-text">
              Descrição acerca do patrocinador. Descrição acerca do
              patrocinador. Descrição acerca do patrocinador. Descrição acerca
              do patrocinador. Descrição acerca do patrocinador.
            </p>
            <router-link
              :to="{ name: 'sponsor' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="mr-2"
            >
              <i class="fas fa-eye"></i> Ver Mais
            </router-link>
          </div>
        </div>
      </div>

      <div class="justify-content-around col-lg-4 col-xs-12 col-md-6 mb-4">
        <div class="card">
          <img src="../assets/animalec.png" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">Patrocinador 6</h5>
            <p class="card-text">
              Descrição acerca do patrocinador. Descrição acerca do
              patrocinador. Descrição acerca do patrocinador. Descrição acerca
              do patrocinador. Descrição acerca do patrocinador.
            </p>
            <router-link
              :to="{ name: 'sponsor' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="mr-2"
            >
              <i class="fas fa-eye"></i> Ver Mais
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </b-row>
</template>

<script>
import { EDIT_SPONSOR } from "@/store/sponsors/sponsor.constants";
import { mapGetters } from "vuex";

export default {
  name: "Sponsor",
  props: ["sponsor"],
  data: function () {
    return {
      color: "",
    };
  },
  methods: {
    ...mapGetters("auth", ["getProfile"]),
    evaluate() {
      if (!this.sponsor.evaluation.includes(this.getProfile()._id)) {
        this.sponsor.evaluation.push(this.getProfile()._id);
        this.color = "red";
      } else {
        this.sponsor.evaluation = this.sponsor.evaluation.filter(
          (user) => user !== this.getProfile()._id
        );
        this.color = "black";
      }
      this.$store.dispatch(`sponsor/${EDIT_SPONSOR}`, this.sponsor).then(
        () => {
          this.$alert(
            `Obrigado por gostares do ${this.sponsor.name}!`,
            "Gosto",
            "success"
          );
        },
        (err) => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    },
  },
  created() {
    if (!this.sponsor.evaluation.includes(this.getProfile()._id)) {
      this.color = "black";
    } else {
      this.color = "red";
    }
  },
};
</script>
