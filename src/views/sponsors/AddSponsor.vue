<template>
  <!-- Portfolio Section -->
  <section class="page-section">
    <b-container>
      <HeaderPage title="Adicionar Patrocinador" />

      <!--FORM-->
      <b-row>
        <form class="row g-3" @submit.prevent="add">
          <div class="col-md-12">
            <label for="name" class="form-label">Nome do Patrocinador</label>
            <input type="text" class="form-control" id="name" value="" required>
          </div>
          <div class="col-md-12">
            <label for="description" class="form-label">Descrição</label>
            <textarea class="form-control" rows="5" id="description" required></textarea>
          </div>
          <div class="col-md-12">
            <label for="motivation" class="form-label">Motivação</label>
            <textarea class="form-control" rows="5" id="motivation" required></textarea>
          </div>
          <div class="col-md-4">
            <label for="photo-1" class="form-label">Foto 1</label>
            <input type="file" accept="image/*" class="form-control" rows="5" id="photo-1">
          </div>
          <div class="col-md-4">
            <label for="photo-2" class="form-label">Foto 2</label>
            <input type="file" accept="image/*" class="form-control" rows="5" id="photo-2"></textarea>
          </div>
          <div class="col-md-4">
            <label for="photo-3" class="form-label">Foto 3</label>
            <input type="file" accept="image/*" class="form-control" rows="5" id="photo-3"></textarea>
          </div>
          <div class="col-md-6">
            <label for="facebook" class="form-label">Link Facebook</label>
            <input class="form-control" id="facebook">
          </div>
          <div class="col-md-6">
            <label for="instagram" class="form-label">Link Instagram</label>
            <input class="form-control" id="instagram">
          </div>
          <div class="col-md-6">
            <label for="twitter" class="form-label">Link Twitter</label>
            <input class="form-control" id="twitter">
          </div>
          <div class="col-md-6">
            <label for="linkedin" class="form-label">Link Linkedin</label>
            <input type="text" class="form-control" id="linkedin">
          </div>
          <div class="col-12">
            <button class="btn btn-outline-primary" type="submit"><span class="fa fa-save"></span> SALVAR</button>
            <router-link
              :to="{ name: 'listSponsors' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="btn btn-outline-danger"
            >
              <i class="fas fa-arrow-circle-left"></i> CANCELAR
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
    HeaderPage,
  },
  data: () => {
    return {
      name: "",
      group: "",
      description: "",
      level: "",
      links: [
        { types: "photo", url: "" },
        { types: "video", url: "" },
        { types: "sound", url: "" },
      ],
      evaluation: [],
      comments: [],
    };
  },
  computed: {
    ...mapGetters("sponsor", ["getMessage"]),
  },
  methods: {
    add() {
      this.$store.dispatch(`sponsor/${ADD_SPONSOR}`, this.$data).then(
        () => {
          this.$alert(this.getMessage, "Patrocinador adicionado!", "success");
          router.push({ name: "listsponsors" });
        },
        (err) => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    },
  },
};
</script>
