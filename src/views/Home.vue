<template>
  <div class="container mt-4">
    <h1 class="text-center my-4 fw-bold">Lista de juegos disponibles</h1>
    <div class="row">
      <div
        v-for="(juego, index) in juegos"
        :key="index"
        class="col-lg-4 col-sm-6 card-group"
      >
      <div class="card">
      <img :src="juego.background_image" class="card-img-top" alt="..." />
      <div class="card-body">
        <h5 class="card-title fw-bold">{{juego.name}}</h5>
      </div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item">Rating: {{juego.rating}}</li>
        <li class="list-group-item">Released: {{juego.released}}</li>
        <li class="list-group-item">Updated: {{juego.updated}}</li>
      </ul>
      <div class="card-body button">
        <button type="button" class="btn btn-info" data-bs-toggle="modal"
              data-bs-target="#modal-opinion"
              @click="cargarJuego(juego.name)">Opinar</button>
      </div>
      </div>
    </div>
    <Modal :juego="juegoSeleccionado"></Modal>
    </div>
  </div>
</template>

<script>
import juegos from "../../games.json";
import Modal from "../components/Modal.vue";

export default {
  components: { Modal },
  data() {
    return {
      juegos: juegos,
      juegoSeleccionado: "",
    };
  },
  methods: {
    cargarJuego(juego) {
      this.juegoSeleccionado = juego;
    },
  },
}
</script>

<style scoped>
.button{
  display: flex;
  justify-content: center;
  align-items: center;
  color: white
}
.card{
  margin-bottom: 20px;
}
</style>