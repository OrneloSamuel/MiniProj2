<template>
  <!-- Portfolio Section -->
  <section class="page-section">
    <b-container>
      <HeaderPage title="Adicionar Patrocinador" />

      <!--FORM-->
      <b-row>
        <form class="row g-3" @submit.prevent="add">
          <div class="col-md-12 form-group">
            <input
              class="form-control"
              id="name"
              v-model="name"
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
              v-model="description"
            ></textarea>
          </div>
          <div class="col-md-12 form-group">
            <textarea
              class="form-control"
              rows="5"
              id="motivation"
              required
              placeholder="Digite a motivação patrocinador"
              v-model="motivation"
            ></textarea>
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              rows="5"
              id="photo-1"
              v-model="photo_one"
              placeholder="Insira o link da foto"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              rows="5"
              id="photo-2"
              v-model="photo_two"
              placeholder="Insira o link da foto"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              rows="5"
              id="photo-3"
              placeholder="Insira o link da foto"
              v-model="photo_three"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="facebook"
              placeholder="Insira o link do facebook"
              v-model="facebook"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="instagram"
              placeholder="Insira o link do instagram"
              v-model="instagram"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="twitter"
              placeholder="Insira o link do twitter"
              v-model="twitter"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              type="text"
              class="form-control"
              id="linkedin"
              placeholder="Insira o link do linkedin"
              v-model="linkedin"
            />
          </div>
          <div class="col-12">
            <button class="btn btn-outline-success mr-2" type="submit">
              <span class="fa fa-save"></span> SALVAR
            </button>
            <router-link
              :to="{ name: 'listSponsors' }"
              tag="button"
              align="center"
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
import { ADD_SPONSOR } from "@/store/sponsors/sponsor.constants";
import HeaderPage from "@/components/HeaderPage.vue";
import router from "@/router";
import { mapGetters } from "vuex";

export default {
  name: "AddSponsor ",
  components: {
    HeaderPage
  },
  data: () => {
    return {
      name: "",
      description: "",
      motivation: "",
      photo_one: "",
      photo_two: "",
      photo_three: "",
      facebook: "",
      instagram: "",
      twitter: "",
      linkedin: "",
      active: true
    };
  },
  computed: {
    ...mapGetters("sponsor", ["getMessage"])
  },
  methods: {
    add() {
      this.$store.dispatch(`sponsor/${ADD_SPONSOR}`, this.$data).then(
        () => {
          this.$alert(this.getMessage, "Patrocinador adicionado!", "success");
          router.push({ name: "listSponsors" });
        },
        err => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    }
  }
};
</script>
