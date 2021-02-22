<template>
  <h1>{{ title }}</h1>
  <div>
    <input type="text" ref="name" />
    <button @click="handleClick()">Click</button>
  </div>
  <p>welcome....</p>

  <teleport to="#modals" v-if="showModal">
    <Modal theme="" @click="toggleModal">
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
      <template v-slot:links>
        <a href="">Sign Up</a>
        <a href="">More Info</a>
      </template>
    </Modal>
  </teleport>

  <teleport to="#modals" v-if="showModalTwo">
    <Modal @click="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>Grab your ninja swag for half price</p>
    </Modal>
  </teleport>

  <button @click.alt="toggleModal">Open Modal (Option)</button>
  <button @click.alt="toggleModalTwo">Open Modal (Option) 2</button>
</template>

<script>
import Modal from "./components/Modal"

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Google Calendar",
      text: "I tried every thing but fail what I want to achieve",
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    handleClick() {
      this.$refs.name.classList.add("active")
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    },
  },
}
</script>

<style>
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
