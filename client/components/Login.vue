<template>
  <div id="bigBox">
    <h2>LOGIN</h2>
    <!-- TODO -->
    <div class="inputBox">
      <form @submit.prevent="loginUser()">
        <div class="inputText">
          <input v-model="email" placeholder="email">
        </div>
        <div class="inputText">
          <input
          type="password" v-model="password"
          placeholder="password"
          >
        </div>
        <button type="submit">Se connecter</button>
      </form>
    </div>
    <router-link to="/register" style="color: #82D7DD">Vous n'avez pas encore un compte ?</router-link>
  </div>
</template>

<script>
module.exports = {
  props: {
    articles: { type: Array, default: [] },
    panier: { type: Object }
  },
  data () {
    return {
      email: '',
      password: ''
    }
  },
  async mounted () {
  },
  methods: {
    async loginUser() {
      this.$emit('login', {
        email: this.email,
        password: this.password
      })
    }
  }
}
</script>

<style scoped>
#bigBox {
  margin: 0 auto;
  margin-top: 200px;
  padding: 20px 50px;
  background-color: rgba(0,0,0,0.8);
  width: 400px;
  height: 300px;
  border-radius: 10px;
  text-align: center;
}
#bigBox h2 {
  color: white;
}
#bigBox .inputBox {
    margin-top: 50px;
} 
#bigBox .inputBox .inputText {
    margin-top: 20px;
}
button[type=submit] {
    width: 150px;
    height: 25px;
    color: white;
    margin-top: 30px;
    border-radius: 20px;
    background-image: linear-gradient(to right, #b8cbb8 0%, #b8cbb8 0%, #b465da 0%, #cf6cc9 33%, #ee609c 66%, #ee609c 100%);
}
</style>
