<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Editar Especialista" />

      <!--FORM-->
      <b-row>
        <form class="row g-3" @submit.prevent="update">
          <div class="col-md-12 form-group">
            <input
              v-model="expert.name"
              class="form-control"
              placeholder="Digite o nome do especialista"
              required
            />
          </div>
          <div class="col-md-12 form-group">
            <textarea
              class="form-control"
              rows="5"
              id="description"
              required
              v-model="expert.description"
              placeholder="Digite a descrição do especialista"
            ></textarea>
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              id="photo-1"
              placeholder="Insira o link da foto"
              v-model="expert.photo_one"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              id="photo-2"
              placeholder="Insira o link da foto"
              v-model="expert.photo_two"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              id="photo-3"
              placeholder="Insira o link da foto"
              v-model="expert.photo_three"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="facebook"
              placeholder="Insira o link do facebook"
              v-model="expert.facebook"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="instagram"
              placeholder="Insira o link do instagram"
              v-model="expert.instagram"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="twitter"
              placeholder="Insira o link do twitter"
              v-model="expert.twitter"
            />
          </div>
          <div class="col-md-6 form-group">
            <input
              class="form-control"
              id="linkedin"
              placeholder="Insira o link do twitter"
              v-model="expert.linkedin"
            />
          </div>
          <div class="col-md-12 form-group">
            <div class="row" v-if="expert.animals.length">
              <div class="col-md-12">
                <h4>Lista de animais</h4>
              </div>
            </div>
          </div>
          <div class="col-md-12">
            <div v-for="(animal, index) in expert.animals" :key="animal.id">
              <div class="row">
                <div class="col-md-4 form-group">
                  <select
                    v-model="animal.animal"
                    :key="index"
                    class="form-control"
                    required
                  >
                    <option
                      v-for="a in myAnimals"
                      :key="a._id"
                      :value="a._id"
                      :selected="true"
                      >{{ a.name }}</option
                    >
                  </select>
                </div>
                <div class="col-md-6 gy-5 form-group">
                  <input
                    class="form-control me-2"
                    id="description-animal"
                    placeholder="Digite a relação com o animal"
                    :key="index"
                    v-model="animal.description"
                  />
                </div>
                <div class="col-md-2 form-group">
                  <button
                    @click="removeAnimal(index)"
                    type="button"
                    class="btn btn-outline-danger mr-2"
                  >
                    <i class="fas fa-trash"></i> REMOVER
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-12">
            <button
              @click="addAnimal"
              type="button"
              class="btn btn-outline-success mr-2"
            >
              <i class="fas fa-plus-square"></i> ADICIONAR ANIMAL
            </button>
            <button class="btn btn-outline-success mr-2" type="submit">
              <span class="fa fa-save"></span> ATUALIZAR
            </button>
            <router-link
              :to="{ name: 'listExperts' }"
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
import { EDIT_EXPERT } from "@/store/experts/expert.constants";
import HeaderPage from "@/components/HeaderPage.vue";
import router from "@/router";
import { FETCH_ANIMALS } from "@/store/animals/animal.constants";
import { mapGetters } from "vuex";

export default {
  name: "EditExpert",
  components: {
    HeaderPage
  },
  data: () => {
    return {
      expert: {},
      myAnimals: []
    };
  },
  computed: {
    ...mapGetters("expert", ["getExpertsById", "getMessage"]),
    ...mapGetters("animal", ["getAnimals"])
  },
  methods: {
    addAnimal() {
      this.expert.animals.push({ id: "" });
    },
    removeAnimal(index) {
      this.expert.animals.splice(index, 1);
    },
    update() {
      this.$store.dispatch(`expert/${EDIT_EXPERT}`, this.$data.expert).then(
        () => {
          this.$alert(this.getMessage, "Especialista atualizado!", "success");
          router.push({ name: "listExperts" });
        },
        err => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    }
  },
  created() {
    this.expert = this.getExpertsById(this.$route.params.expertId);
    this.$store.dispatch(`animal/${FETCH_ANIMALS}`).then(
      () => {
        this.myAnimals = this.getAnimals;
      },
      err => {
        this.$alert(`${err.message}`, "Erro", "error");
      }
    );
  }
};
</script>
