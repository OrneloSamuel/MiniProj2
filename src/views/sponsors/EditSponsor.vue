<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Editar Patrocinador" />

      <!--FORM-->
      <b-row>
        <form class="row g-3" @submit.prevent="update">
          <div class="col-md-12 form-group">
            <input
              class="form-control"
              id="name"
              v-model="sponsor.name"
              required
              placeholder="Digite o nome do patrocinador"
            />
          </div>
          <div class="col-md-12 form-group">
            <textarea
              class="form-control"
              rows="5"
              id="description"
              required
              placeholder="Digite a descrição patrocinador"
              v-model="sponsor.description"
            ></textarea>
          </div>
          <div class="col-md-12 form-group">
            <textarea
              class="form-control"
              rows="5"
              id="motivation"
              required
              placeholder="Digite a motivação patrocinador"
              v-model="sponsor.motivation"
            ></textarea>
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              rows="5"
              id="photo-1"
              v-model="sponsor.photo_one"
              placeholder="Insira o link da foto"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              rows="5"
              id="photo-2"
              v-model="sponsor.photo_two"
              placeholder="Insira o link da foto"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              rows="5"
              id="photo-3"
              placeholder="Insira o link da foto"
              v-model="sponsor.photo_three"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="facebook"
              placeholder="Insira o link do facebook"
              v-model="sponsor.facebook"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="instagram"
              placeholder="Insira o link do instagram"
              v-model="sponsor.instagram"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="twitter"
              placeholder="Insira o link do twitter"
              v-model="sponsor.twitter"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              type="text"
              class="form-control"
              id="linkedin"
              placeholder="Insira o link do linkedin"
              v-model="sponsor.linkedin"
            />
          </div>
          <div class="col-12">
            <button class="btn btn-outline-success mr-2" type="submit">
              <span class="fa fa-save"></span> ATUALIZAR
            </button>
            <router-link
              :to="{ name: 'listSponsors' }"
              tag="button"
              class="btn btn-outline-danger"
            >
              <i class="fas fa-window-close"></i> CANCELAR
            </router-link>
          </div>
        </form>
      </b-row>
    </b-container>
  </section>
</template>

<script>
import { EDIT_SPONSOR } from "@/store/sponsors/sponsor.constants";
import HeaderPage from "@/components/HeaderPage.vue";
import router from "@/router";
import { mapGetters } from "vuex";

export default {
  name: "EditSponsor",
  components: {
    HeaderPage
  },
  data: () => {
    return {
      sponsor: {}
    };
  },
  computed: {
    ...mapGetters("sponsor", ["getSponsorsById", "getMessage"])
  },
  methods: {
    update() {
      this.$store.dispatch(`sponsor/${EDIT_SPONSOR}`, this.$data.sponsor).then(
        () => {
          this.$alert(this.getMessage, "Patrocinador atualizado!", "success");
          router.push({ name: "listSponsors" });
        },
        err => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    }
  },
  created() {
    this.sponsor = this.getSponsorsById(this.$route.params.sponsorId);
  }
};
</script>
