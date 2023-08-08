<!-- HTML -->
<template>
  <h2>{{title}}</h2>
  <p>Welcome...</p>
  <div v-if="showModal">
    <Modal to="#modals" theme="sale" @close="toggleModal" >
      <template v-slot:links>
        <a href="#">Sign up</a>
        <a href="#">Register</a>
      </template>
      <h1>{{header}}</h1>
      <p>{{text}}</p>
    </Modal>    
  </div>
  <teleport to="#modals" v-if="showModal2">
    <Modal @close="toggleModal2">      
      <h2>Thanks for your patronage</h2>
      <p>Sing in to get the latest features</p>
    </Modal>
  </teleport>
  <button @click.alt="toggleModal">Open Modal(alt)</button>
  <button @click.alt="toggleModal2">Open Modal2(alt)</button>
</template>

<!-- SCRIPT -->
<script>
import Modal from "./components/Modal"

export default {
  name: 'App',
  components:{
    Modal
  },
  data() {
    return {
      title: "My first Vue App:)",
      header: "Sign up for the give away",
      text: "Grab your swag Fam, for half price",
      showModal: false,
      showModal2: false
    }
  },
  methods: {
    toggleModal() {
      return this.showModal = !this.showModal
    },
    toggleModal2() {
      return this.showModal2 = !this.showModal2
    }
  }
}
</script>

<!-- CSS -->
<style>
#app, #modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h2{
  border-bottom: 1px solid rgb(190, 190, 190);
  padding-bottom: 10px;
  display: inline-block;
}
</style>
