<template>
  <!--/ <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> /-->
  <h1>{{ title }}</h1><br>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>

  <!--/ THE 'to' ATTR IN teleport WAS EXLUSIVE ON teleport ONLY AND THE VALUE OF IT IS WHERE YOU WANT TO TELEPORT IT (ID OR CLASS OF THAT ELEMENT)/-->
  <teleport to="#modals" v-if="showModal"><!--/ THIS teleport TAG WAS PREVIOUSLY div. IT WAS CHANGED INTO teleport TO DEMO HOW TO USE THIS FEATURE OF VUE JS /-->
    <Modal theme="sale" @close="toggleModal"><!--/ THIS IS AN EXAMPLE OF VUE JS SLOT /-->
      <h1>This is a modal</h1>
      <p>Lorem ipsum dolor sit amet consectetur.</p>

      <!--/ NAMED SLOTS /-->
      <!--/ THIS TEMPLATE FOR SLOT CAN BE PLACED ANYWHERE INSIDE OF THIS <MODAL> /-->
      <template v-slot:links><!--/ THIS IS HOW WE GIVE NAME TO A SLOT /-->
        <a href="https://sites.google.com/view/madriancomlab/home">Google Site Portfolio</a>
        <a href="https://github.com/madrinanComLab">GitHub Account</a>
      </template>
    </Modal>

    <!--/ <Modal 
      :header="header"
      :text="text" 
      theme="sale"
      :books="books"
      :authors="['José Rizal', 'Ambeth Ocampo', 'John Ray Ramos']"
      @close="toggleModal"/> /-->
  </teleport>

  <teleport to="#modals" v-if="showModalTwo"><!--/ THIS teleport TAG WAS PREVIOUSLY div. IT WAS CHANGED INTO teleport TO DEMO HOW TO USE THIS FEATURE OF VUE JS /-->
    <!--/ THE SECOND <Modal> BELOW DEMONSTRATE HOW TO REUSE A COMPONENT /-->
    <Modal @close="closeSecondModal">
      <h1>This is the second modal</h1>
      <p>Lorem ipsum dolor sit amet consectetur.</p>

      <template v-slot:links>
        <a href="#">Button #1</a>
        <a href="#">Button #2</a>
      </template>
    </Modal>
  </teleport>

  <br>
  <button @click="toggleModal">Show Modal</button>
  <button @click="closeSecondModal">Show Second Modal</button>

  <!--/
  CLICK EVENT MODIFIER

  <button @click.right="toggleModal">Show Modal</button> THIS WILL ONLY TRIGGER IF USER PRESS RIGHT CLICK
  <button @click.shift="toggleModal">Show Modal</button> THIS WILL ONLY TRIGGER IF USER HOLDS SHIFT WHILE PRESSING LEFT CLICK
  <button @click.alt="toggleModal">Show Modal</button> THIS WILL ONLY TRIGGER IF USER HOLDS ALT WHILE PRESSING LEFT CLICK
  <button @click.self="toggleModal">Show Modal</button> THIS IS EFFECTIVE IN ELEMENTS THAT HAS CHILD IN IT, THIS MEANS IT WILL ONLY TRIGGER IF THE PARENT TAG WAS CLICKED AND NOT ITS CHILD
  /-->

  <!--/
  <Modal 
    :header="header"<---- THIS IS CALLED 'PROP'. THE DATA WE PASS TO A COMPONENT
    :text="text" <------- THIS IS HOW YOU PASS VARIABLE AS PROP
    theme="sale"
    :books="books" NOTE: DECLARING PROPS HERE ARE OPTIONAL IF IT DOESN'T HAVE VALUE TO HOLD
    @close="toggleModal"/> THE @close WAS THE CUSTOM EVENT THAT WE DEFINE IN Modal.vue
  /-->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Modal from "./components/Modal.vue" // IT WAS NECESSARY TO IMPORT IT

export default {
  name: 'App',
  components: { Modal }, // ALSO REGISTER IT HERE
  data() {
    return {
      title: "My First Vue App :3",
      header: "Sign Up Now!",
      text: "Tangna Baho dito sa Outpost!",
      showModal: false,
      showModalTwo: false,
      books: [
        "The Reign of Greed",
        "Rizal Without the Overcoat",
        "Bayani Biographies: Andres Bonifacio"
      ]
      /* books: [
          { title: "The Reign of Greed", author: "José Rizal", id: 0 },
          { title: "Rizal Without the Overcoat", author: "Ambeth Ocampo", id: 1 },
          { title: "Bayani Biographies: Andres Bonifacio", author: "John Ray Ramos", id: 2 },
      ] */
    }
  },

  methods: {
    handleClick() {
      // NOTE: 'name' IN this.$refs.name WAS THE ref VALUE WE ASSIGNED IN THE INPUT TAG
      console.log(this.$refs.name.value)
      this.$refs.name.classList.add("active")
      this.$refs.name.focus()
      this.title = this.$refs.name.value
    },

    toggleModal() {
      this.showModal = !this.showModal
    },

    closeSecondModal() {
      this.showModalTwo = !this.showModalTwo
    }
  }
  /* components: {
    HelloWorld
  } */
}
</script>

<style>
#app, #modals { /* THE #modals WAS ADDED WHEN WE TELEPORT THE MODAL COMPONENT (Modal.vue) TO #modal ELEMENT IN index.html THAT YOU'LL FOUND IN PUBLIC FOLDER */
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #DDD;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
