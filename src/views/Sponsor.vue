<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="PATROCINADOR 1" />
      <b-row>
        <div class="row row-cols-lg-2 row-cols-md-2 row-cols-1 gy-5">
          <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
            <img src="../assets/animalec.png" class="d-block w-100" alt="..." />
          </div>

          <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
            <h3 class="ps-5">Descrição</h3>

            <p>
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. Descrição completa do patrocinador. Descrição
              completa do patrocinador. Descrição completa do patrocinador.
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. Descrição completa do patrocinador. Descrição
              completa do patrocinador. Descrição completa do patrocinador.
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. Descrição completa do patrocinador. Descrição
              completa do patrocinador. Descrição completa do patrocinador.
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. <br /><br />
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. Descrição completa do patrocinador. Descrição
              completa do patrocinador. Descrição completa do patrocinador.
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. Descrição completa do patrocinador. Descrição
              completa do patrocinador. Descrição completa do patrocinador.
              Descrição completa do patrocinador.
              <br /><br />
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. Descrição completa do patrocinador. Descrição
              completa do patrocinador. Descrição completa do patrocinador.
              Descrição completa do patrocinador. Descrição completa do
              patrocinador. Descrição completa do patrocinador.
            </p>
          </div>

          <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
            <img
              src="../assets/animalec2.png"
              class="d-block w-100"
              alt="..."
            />
          </div>

          <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
            <h3 class="ps-5">Motivação</h3>

            <p>
              O que motiva a patrocinar. O que motiva a patrocinar. O que motiva
              a patrocinar. O que motiva a patrocinar. O que motiva a
              patrocinar. O que motiva a patrocinar. O que motiva a patrocinar.
              O que motiva a patrocinar. O que motiva a patrocinar. O que motiva
              a patrocinar. O que motiva a patrocinar. O que motiva a
              patrocinar. O que motiva a patrocinar. O que motiva a patrocinar.
              O que motiva a patrocinar. O que motiva a patrocinar. O que motiva
              a patrocinar. O que motiva a patrocinar. O que motiva a
              patrocinar. O que motiva a patrocinar. O que motiva a patrocinar.
              O que motiva a patrocinar. O que motiva a patrocinar. <br /><br />
              O que motiva a patrocinar. O que motiva a patrocinar. O que motiva
              a patrocinar. O que motiva a patrocinar. O que motiva a
              patrocinar. O que motiva a patrocinar. O que motiva a patrocinar.
              O que motiva a patrocinar. O que motiva a patrocinar. O que motiva
              a patrocinar. O que motiva a patrocinar.
            </p>
          </div>

          <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
            <img src="../assets/animalec.png" class="d-block w-100" alt="..." />
          </div>

          <div class="justify-content-around col-lg-6 col-xs-12 col-md-6">
            <h3 class="ps-5">Nossas Páginas</h3>

            <div class="mt-5 text-center">
              <div class="row">
                <div class="col-3 col-xs-3 col-sm-3">
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
        </div>

        <div class="row col-12 mt-5">
          <div class="text-center col-lg-12 col-12">
            <router-link
              :to="{ name: 'sponsors' }"
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
import { EDIT_SPONSOR } from "@/store/sponsors/sponsor.constants";
import { mapGetters } from "vuex";
export default {
  name: "sponsor",
  components: {
    HeaderPage,
  },
  data: function () {
    return {
      sponsor: "",
      comment: "",
    };
  },
  computed: {
    ...mapGetters("sponsor", ["getsponsorsById", "getMessage"]),
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
      for (let comment of this.sponsor.comments) {
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
      this.sponsor.comments.push({
        body: this.comment,
        user: this.getProfile._id,
        date: this.getCurrentDateTime(),
      });
      this.$store.dispatch(`sponsor/${EDIT_SPONSOR}`, this.sponsor).then(
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
  },
  created() {
    this.sponsor = this.getsponsorsById(this.$route.params.sponsorId);
  },
};
</script>
