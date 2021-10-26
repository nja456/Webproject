<template>
  <div>
    <ul>
      <li v-for="article of panier.articles" :key="article.id">
        {{ find(article.id).name}} - {{ find(article.id).description }}
      </li>
    </ul>
    <div v-if="isConnected">
      <h2>Mon Panier</h2>
      <button @click="pay">Payer</button>
    </div>
    <div v-else id="bigBox">
      <img src="https://i.ibb.co/wBFCC3L/image.png" width="150" height="150"/>
      <p>Vous ne semblez pas être connecté à votre compte ? Cliquez ici :</p>
      <router-link to="/login">Se connecter pour payer</router-link>
    </div>
  </div>
</template>

<script>
module.exports = {
  props: {
    articles: { type: Array, default: [] },
    panier: { type: Object },
    isConnected: { type: Boolean }
  },
  data () {
    return {
    }
  },
  async mounted () {
  },
  methods: {
    find (articleId) {
      return this.articles.find(article => article.id === articleId)
    },
    pay () {
      this.$emit('pay')
    }
  }
}
</script>

<style scoped>
#bigBox{
  margin: 0 auto;
  margin-top: 200px;
  padding: 20px 50px;
  background-color: rgba(216,221,222,0.8);
  width: 420px;
  height: 280px;
  border-radius: 10px;
  text-align: center;
}
</style>
