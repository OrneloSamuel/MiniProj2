<template>
  <b-row>
    <div class="row row-cols-lg-3 row-cols-md-3 row-cols-1 gy-4">
      <div class="justify-content-around col-lg-4 col-xs-12 col-md-6 mb-4">
        <div class="card">
          <img src="../assets/animalec.png" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">Especialista 1</h5>
            <p class="card-text">
              Descrição acerca do especialista. Descrição acerca do
              especialista. Descrição acerca do especialista. Descrição acerca
              do especialista. Descrição acerca do especialista.
            </p>
            <router-link
              :to="{name: 'expert'}"
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
            <h5 class="card-title">Especialista 2</h5>
            <p class="card-text">
              Descrição acerca do especialista. Descrição acerca do
              especialista. Descrição acerca do especialista. Descrição acerca
              do especialista. Descrição acerca do especialista.
            </p>
            <router-link
              :to="{name: 'expert'}"
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
            <h5 class="card-title">Especialista 3</h5>
            <p class="card-text">
              Descrição acerca do especialista. Descrição acerca do
              especialista. Descrição acerca do especialista. Descrição acerca
              do especialista. Descrição acerca do especialista.
            </p>
            <router-link
              :to="{name: 'expert'}"
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
            <h5 class="card-title">Especialista 4</h5>
            <p class="card-text">
              Descrição acerca do especialista. Descrição acerca do
              especialista. Descrição acerca do especialista. Descrição acerca
              do especialista. Descrição acerca do especialista.
            </p>
            <router-link
              :to="{name: 'expert'}"
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
            <h5 class="card-title">Especialista 5</h5>
            <p class="card-text">
              Descrição acerca do especialista. Descrição acerca do
              especialista. Descrição acerca do especialista. Descrição acerca
              do especialista. Descrição acerca do especialista.
            </p>
            <router-link
              :to="{name: 'expert'}"
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
            <h5 class="card-title">Especialista 6</h5>
            <p class="card-text">
              Descrição acerca do especialista. Descrição acerca do
              especialista. Descrição acerca do especialista. Descrição acerca
              do especialista. Descrição acerca do especialista.
            </p>
            <router-link
              :to="{name: 'expert'}"
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
import { EDIT_EXPERT } from "@/store/experts/expert.constants";
import { mapGetters } from "vuex";

export default {
  name: "Expert",
  props: ["expert"],
  data: function () {
    return {
      color: "",
    };
  },
  methods: {
    ...mapGetters("auth", ["getProfile"]),
    evaluate() {
      if (!this.expert.evaluation.includes(this.getProfile()._id)) {
        this.expert.evaluation.push(this.getProfile()._id);
        this.color = "red";
      } else {
        this.expert.evaluation = this.expert.evaluation.filter(
          (user) => user !== this.getProfile()._id
        );
        this.color = "black";
      }
      this.$store.dispatch(`expert/${EDIT_EXPERT}`, this.expert).then(
        () => {
          this.$alert(
            `Obrigado por gostares do ${this.expert.name}!`,
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
    if (!this.expert.evaluation.includes(this.getProfile()._id)) {
      this.color = "black";
    } else {
      this.color = "red";
    }
  },
};
</script>
