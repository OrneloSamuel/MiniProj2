<template>
  <!-- Portfolio Section -->
  <section class="page-section">
    <b-container>
      <HeaderPage title="Adicionar Especialista" />

      <!--FORM-->
      <b-row>
        <form class="row g-3" @submit.prevent="add">
          <div class="col-md-12 form-group">
            <input
              v-model="name"
              class="form-control"
              id="name"
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
              v-model="description"
              placeholder="Digite a descrição do especialista"
            ></textarea>
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              id="photo-1"
              placeholder="Insira o link da foto"
              v-model="photo_one"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
              id="photo-2"
              placeholder="Insira o link da foto"
              v-model="photo_two"
            />
          </div>
          <div class="col-md-4 form-group">
            <input
              class="form-control"
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
              class="form-control"
              id="linkedin"
              placeholder="Insira o link do twitter"
              v-model="linkedin"
            />
          </div>
          <div class="col-md-12 form-group">
            <div class="row" v-if="animals.length">
              <div class="col-md-12">
                <h4>Lista de animais</h4>
              </div>
            </div>
          </div>
          <div class="col-md-12">
            <div v-for="(animal, index) in animals" :key="animal.id">
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
              <span class="fa fa-save"></span> SALVAR
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
import { ADD_EXPERT } from "@/store/experts/expert.constants";
import { FETCH_ANIMALS } from "@/store/animals/animal.constants";
import HeaderPage from "@/components/HeaderPage.vue";
import router from "@/router";
import { mapGetters } from "vuex";

export default {
  name: "AddExpert",
  components: {
    HeaderPage
  },
  data: () => {
    return {
      name: "",
      description: "",
      photo_one: "",
      photo_two: "",
      photo_three: "",
      facebook: "",
      instagram: "",
      twitter: "",
      linkedin: "",
      animals: [],
      myAnimals: [],
      active: true
    };
  },
  computed: {
    ...mapGetters("expert", ["getMessage"]),
    ...mapGetters("animal", ["getAnimals", "getMessage"])
  },
  methods: {
    addAnimal() {
      this.animals.push({ animal: "", description: "" });
    },
    removeAnimal(index) {
      this.animals.splice(index, 1);
    },
    add() {
      this.$store.dispatch(`expert/${ADD_EXPERT}`, this.$data).then(
        () => {
          this.$alert(this.getMessage, "Especialista adicionado!", "success");
          router.push({ name: "listExperts" });
        },
        err => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    }
  },
  created() {
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
