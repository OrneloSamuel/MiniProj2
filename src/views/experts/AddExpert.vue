<template>
  <!-- Portfolio Section -->
  <section class="page-section">
    <b-container>
      <HeaderPage title="Adicionar Especialista" />

      <!--FORM-->
      <b-row>
        <form class="row g-3" @submit.prevent="add">
          <div class="col-md-12">
            <label for="name" class="form-label">Nome do Especialista</label>
            <input
              v-model="name"
              class="form-control"
              id="name"
              value=""
              required
            />
          </div>
          <div class="col-md-12">
            <label for="description" class="form-label">Descrição</label>
            <textarea
              class="form-control"
              rows="5"
              id="description"
              required
              v-model="description"
            ></textarea>
          </div>
          <div class="col-md-4">
            <label for="photo-1" class="form-label">Foto 1</label>
            <input
              type="file"
              accept="image/*"
              class="form-control"
              rows="5"
              id="photo-1"
            />
          </div>
          <div class="col-md-4">
            <label for="photo-2" class="form-label">Foto 2</label>
            <input
              type="file"
              accept="image/*"
              class="form-control"
              rows="5"
              id="photo-2"
            />
          </div>
          <div class="col-md-4">
            <label for="photo-3" class="form-label">Foto 3</label>
            <input
              type="file"
              accept="image/*"
              class="form-control"
              rows="5"
              id="photo-3"
            />
          </div>
          <div class="col-md-6">
            <label for="facebook" class="form-label">Link Facebook</label>
            <input class="form-control" id="facebook" />
          </div>
          <div class="col-md-6">
            <label for="instagram" class="form-label">Link Instagram</label>
            <input class="form-control" id="instagram" />
          </div>
          <div class="col-md-6">
            <label for="twitter" class="form-label">Link Twitter</label>
            <input class="form-control" id="twitter" />
          </div>
          <div class="col-md-6">
            <label for="linkedin" class="form-label">Link Linkedin</label>
            <input type="text" class="form-control" id="linkedin" />
          </div>
          <div class="col-md-4">
            <label for="linkedin" class="form-label">Adicionar Animais</label>
            <input
              class="form-control me-2"
              type="search"
              placeholder="Digite o nome do animal"
              aria-label="Search"
            />
          </div>
          <div class="col-md-6 gy-5">
            <input
              class="form-control me-2"
              id="description-animal"
              placeholder="Digite a relação com o animal"
            />
          </div>
          <div class="col-md-2 gy-5">
            <button class="btn btn-outline-secondary" type="button">
              <span class="fa fa-plus-square"></span> Adicionar Animal
            </button>
          </div>
          <table class="table table-striped">
            <thead class="table-dark">
              <tr>
                <th scope="col">#</th>
                <th scope="col">Animal</th>
                <th scope="col">Relação</th>
              </tr>
            </thead>
          </table>
          <div class="col-12">
            <button class="btn btn-outline-primary" type="submit">
              <span class="fa fa-save"></span> SALVAR
            </button>
            <router-link
              :to="{ name: 'listExperts' }"
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
import { ADD_EXPERT } from "@/store/experts/expert.constants";
import HeaderPage from "@/components/HeaderPage.vue";
import router from "@/router";
import { mapGetters } from "vuex";

export default {
  name: "AddExpert",
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
    ...mapGetters("expert", ["getMessage"]),
  },
  methods: {
    add() {
      this.$store.dispatch(`expert/${ADD_EXPERT}`, this.$data).then(
        () => {
          this.$alert(this.getMessage, "Especialista adicionado!", "success");
          router.push({ name: "listExperts" });
        },
        (err) => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    },
  },
};
</script>
