<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="EXPECIALISTA 1" />
      <b-row>
        <div class="row row-cols-lg-2 row-cols-md-2 row-cols-1 gy-5">
          <div class="justify-content-around col-lg-6 col-xs-12 col-md-6 mb-4">
            <b-carousel
              id="carousel-1"
              v-model="slide"
              :interval="4000"
              controls
              indicators
              background="#ababab"
              style="text-shadow: 1px 1px 2px #333"
              @sliding-start="onSlideStart"
              @sliding-end="onSlideEnd"
            >
              <b-carousel-slide>
                <template #img>
                  <img
                    class="d-block img-fluid w-100"
                    width="1024"
                    height="480"
                    src="../assets/animalec.png"
                    alt="image slot"
                  />
                </template>
              </b-carousel-slide>
              <b-carousel-slide>
                <template #img>
                  <img
                    class="d-block img-fluid w-100"
                    width="1024"
                    height="480"
                    src="../assets/animalec2.png"
                    alt="image slot"
                  />
                </template>
              </b-carousel-slide>
            </b-carousel>
          </div>

          <div class="col-lg-6 col-xs-12 col-md-6 mb-4">
            <h3 class="ps-5">Descrição</h3>

            <p>
              Descrição completa do especialista. Descrição completa do
              especialista. Descrição completa do especialista. Descrição
              completa do especialista. Descrição completa do especialista.
              Descrição completa do especialista. Descrição completa do
              especialista. Descrição completa do especialista. Descrição
              completa do especialista. Descrição completa do especialista.
              Descrição completa do especialista. Descrição completa do
              especialista. Descrição completa do especialista. Descrição
              completa do especialista. Descrição completa do especialista.
              Descrição completa do especialista. Descrição completa do
              especialista. <br /><br />
              Descrição completa do especialista. Descrição completa do
              especialista. Descrição completa do especialista. Descrição
              completa do especialista. Descrição completa do especialista.
              Descrição completa do especialista. Descrição completa do
              especialista. Descrição completa do especialista. Descrição
              completa do especialista. Descrição completa do especialista.
              Descrição completa do especialista. Descrição completa do
              especialista. Descrição completa do especialista. Descrição
              completa do especialista. Descrição completa do especialista.
              Descrição completa do especialista. Descrição completa do
              especialista.
            </p>
          </div>
        </div>

        <div class="row mt-4">
          <h3 class="card-title ps-5">Especialidades</h3>
        </div>

        <div class="row row-cols-lg-2 col-12 gy-4 mt-2">
          <div class="col-4">
            <div class="list-group" id="list-tab" role="tablist">
              <a
                class="list-group-item list-group-item-action active"
                id="list-home-list"
                data-bs-toggle="list"
                href="#list-home"
                role="tab"
                aria-controls="list-home"
                >Animal 1</a
              >
              <a
                class="list-group-item list-group-item-action"
                id="list-profile-list"
                data-bs-toggle="list"
                href="#list-profile"
                role="tab"
                aria-controls="list-profile"
                >Animal 2</a
              >
              <a
                class="list-group-item list-group-item-action"
                id="list-messages-list"
                data-bs-toggle="list"
                href="#list-messages"
                role="tab"
                aria-controls="list-messages"
                >Animal 3</a
              >
              <a
                class="list-group-item list-group-item-action"
                id="list-settings-list"
                data-bs-toggle="list"
                href="#list-settings"
                role="tab"
                aria-controls="list-settings"
                >Animal 4</a
              >
            </div>
          </div>

          <div class="col-8">
            <div class="tab-content" id="nav-tabContent">
              <div
                class="tab-pane fade show active"
                id="list-home"
                role="tabpanel"
                aria-labelledby="list-home-list"
              >
                <h4 class="card-title">Animal 1</h4>
                <p>
                  Descrição sobre a relação ou experiência com o animal 1.
                  Descrição sobre a relação ou experiência com o animal 1.
                  Descrição sobre a relação ou experiência com o animal 1.
                  Descrição sobre a relação ou experiência com o animal 1.
                  Descrição sobre a relação ou experiência com o animal 1.
                  Descrição sobre a relação ou experiência com o animal 1.
                </p>
              </div>
              <div
                class="tab-pane fade"
                id="list-profile"
                role="tabpanel"
                aria-labelledby="list-profile-list"
              >
                <h4 class="card-title">Animal 2</h4>
                <p>
                  Descrição sobre a relação ou experiência com o animal 2.
                  Descrição sobre a relação ou experiência com o animal 2.
                  Descrição sobre a relação ou experiência com o animal 2.
                  Descrição sobre a relação ou experiência com o animal 2.
                  Descrição sobre a relação ou experiência com o animal 2.
                  Descrição sobre a relação ou experiência com o animal 2.
                  Descrição sobre a relação ou experiência com o animal 2.
                </p>
              </div>
              <div
                class="tab-pane fade"
                id="list-messages"
                role="tabpanel"
                aria-labelledby="list-messages-list"
              >
                <h4 class="card-title">Animal 3</h4>
                <p>
                  Descrição sobre a relação ou experiência com o animal 3.
                  Descrição sobre a relação ou experiência com o animal 3.
                  Descrição sobre a relação ou experiência com o animal 1.
                  Descrição sobre a relação ou experiência com o animal 3.
                </p>
              </div>
              <div
                class="tab-pane fade"
                id="list-settings"
                role="tabpanel"
                aria-labelledby="list-settings-list"
              >
                <h4 class="card-title">Animal 4</h4>
                <p>
                  Descrição sobre a relação ou experiência com o animal 4.
                  Descrição sobre a relação ou experiência com o animal 4.
                  Descrição sobre a relação ou experiência com o animal 4.
                  Descrição sobre a relação ou experiência com o animal 4.
                  Descrição sobre a relação ou experiência com o animal 4.
                  Descrição sobre a relação ou experiência com o animal 4.
                </p>
              </div>
            </div>
          </div>
        </div>

        <div class="row col-12 col-lg-6">
          <div class="col-lg-12 col-12 mt-5">
            <h3 class="ps-5">Nossas Páginas</h3>

            <div class="row mt-4">
              <div class="col-3">
                <a href="#"
                  ><span class="fab fa-facebook fa-2x text-primary"></span
                ></a>
              </div>
              <div class="col-3">
                <a href="#"
                  ><span class="fab fa-instagram fa-2x text-primary"></span
                ></a>
              </div>
              <div class="col-3">
                <a href="#"
                  ><span class="fab fa-twitter fa-2x text-primary"></span
                ></a>
              </div>
              <div class="col-3">
                <a href="#"
                  ><span class="fab fa-linkedin fa-2x text-primary"></span
                ></a>
              </div>
            </div>
          </div>
        </div>

        <div class="row col-12 mt-5">
          <div class="col-lg-12 col-12 text-center">
            <router-link
              :to="{ name: 'experts' }"
              tag="b-button"
              variant="outline-success"
              align="center"
              class="btn btn-primary"
            >
              <i class="fas fa-arrow-circle-left"></i> VOLTAR
            </router-link>
          </div>
        </div>
      </b-row>
    </b-container>
  </section>
</template>

<script>
import HeaderPage from "@/components/HeaderPage.vue";
import { EDIT_EXPERT } from "@/store/experts/expert.constants";
import { mapGetters } from "vuex";
export default {
  name: "Expert",
  components: {
    HeaderPage,
  },
  data: function () {
    return {
      expert: "",
      comment: "",
      slide: 0,
      sliding: null,
    };
  },
  computed: {
    ...mapGetters("expert", ["getExpertsById", "getMessage"]),
    ...mapGetters("auth", ["getProfile"]),
    ...mapGetters("user", ["getUsersById", "getNameById"]),
    ...mapGetters(["getUserLevelByPoints"]),
  },
  methods: {
    showVideo(videoUrl) {
      this.$fire({
        title: "<strong>Vídeo</strong>",
        icon: "info",
        html: `
          <iframe width='460' height='315' 
            src='${videoUrl}' frameborder='0' 
            allow='accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture'
            allowfullscreen></iframe> 
          `,
        focusConfirm: false,
        confirmButtonText: '<i class="fa fa-thumbs-up"></i> OK',
      });
    },
    showComments() {
      this.$fire({
        title: "<strong>Comentários</strong>",
        icon: "info",
        html: this.generateComments(),
        focusConfirm: false,
        confirmButtonText: '<i class="fa fa-thumbs-up"></i> OK',
      });
    },
    generateComments() {
      let comments = "";
      for (let comment of this.expert.comments) {
        comments += `
        <b-alert show variant="secondary">
          
          
          <b>${comment.user.name}</b> (${comment.date})<br>
          ${comment.body}  
        </b-alert>
        <br><br>
          `;
      }
      return comments;
    },
    setComment() {
      this.expert.comments.push({
        body: this.comment,
        user: this.getProfile._id,
        date: this.getCurrentDateTime(),
      });
      this.$store.dispatch(`expert/${EDIT_EXPERT}`, this.expert).then(
        () => {
          this.$alert(`Obrigado pelo comentário!`, "Comentários", "success");
        },
        (err) => {
          this.$alert(`${err.message}`, "Erro", "error");
        }
      );
    },
    getCurrentDateTime() {
      const today = new Date();
      const date =
        today.getFullYear() +
        "-" +
        (today.getMonth() + 1) +
        "-" +
        today.getDay();
      const time = today.getHours() + ":" + today.getMinutes();
      return `${date} ${time}`;
    },
    setCurrentDateTime(commentDate) {
      const date = new Date(commentDate);
      const formatDate =
        date.getFullYear() + "-" + (date.getMonth() + 1) + "-" + date.getDay();
      const formatTime = date.getHours() + ":" + date.getMinutes();
      return `${formatDate} ${formatTime}`;
    },
    /*onSlideStart(slide) {
      this.sliding = true
    },
    onSlideEnd(slide) {
      this.sliding = false
    }*/
  },
  created() {
    this.expert = this.getExpertsById(this.$route.params.expertId);
  },
};
</script>
