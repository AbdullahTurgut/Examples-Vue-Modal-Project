<template>
    <h1> {{ title }} </h1>
    <!-- <br>
    <input type="text" ref="name">
    <button @click="handleClick">Click Here</button> -->
    <teleport to=".modals" v-if="showModal" >
      <Modal theme="sale" @close="toggleModal" >
        <template v-slot:links>
          <a href="#">sign up now</a>
          <a href="#">more info</a>
        </template>
        <h1>Ninja Getaway!</h1>
        <p>Grab your ninja swag for half price!</p>
        </Modal>
    </teleport>

    <teleport to=".modals" v-if="showModalTwo" >
      <Modal @close="toggleModalTwo" >
        <h1>Sign up to the newsletter</h1>
        <p>For updates and promo codes!</p>
      </Modal>
    </teleport>


    <br>
    <button @click.alt="toggleModal">Open Modal(When The Alt Key Down)</button>
    <button @click="toggleModalTwo">Open Modal Two</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components:{
    Modal
  },
  data() {
    return {
      title: 'My First Vue App',
      showModal : false,
      showModalTwo:false,
    }
  },
  methods:{
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModalTwo(){
      this.showModalTwo = !this.showModalTwo
    }
    // handleClick(){
    //   console.log(this.$refs.name)
    //   // active clası eklemek için input alanına
    //   this.$refs.name.classList.add('active')
    //   //input alanına odaklama yapar
    //   this.$refs.name.focus()
    // }
  }
}
</script>

<style >
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
