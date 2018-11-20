<template>
  <div id='app'>
    <Header />
    <main>
      <div id='app-body'>
        <DrinkCard :recipe='currentRecipe'/>
        <ButtonContainer :getRecipe='getRecipe' :apiURL='apiURL' :recipe='currentRecipe' :currentComments='currentComments' :getComments='getComments'/>
      </div>
    </main>
    <Footer />
  </div>
</template>

<script>
import DrinkCard from './components/DrinkCard'
import ButtonContainer from './components/ButtonContainer'
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    DrinkCard,
    ButtonContainer,
    Header,
    Footer
  },
  data() {
    return {
      apiURL: 'https://drinks-backend.herokuapp.com/',
      comments: [],
      drinkData: [],
      currentRecipe: {},
      currentComments: [],
      lastTenDrinks: []
    }
  },
  mounted() {
    this.getRecipe()
  },
  methods: {
    getRecipe() {
      fetch(this.apiURL)
        .then(res => res.json())
        .then(res => {
          this.recipeData = res.recipes
          this.chooseRandomRecipe()
          this.getComments()
          return res
        })
    },
    getComments() {
      fetch(this.apiURL + 'comments')
        .then(res => res.json())
        .then(json => {
          this.comments = json.comments
          this.getCommentsForCurrentDrink()
          return json
        })
    },
    chooseRandomRecipe() {
      let tempNum = Math.floor(Math.random() * this.recipeData.length)
      let drinkId = this.recipeData[tempNum].drink_id
      if(this.lastTenDrinks.includes(drinkId)){
        console.log('repeat', drinkId)
        this.chooseRandomRecipe()
      } else {
        this.setLengthOfLastTenDrinks()
        this.lastTenDrinks.push(drinkId)
        this.currentRecipe = this.recipeData[tempNum]
        return this.lastTenDrinks
      }
    },
    setLengthOfLastTenDrinks() {
      if(this.lastTenDrinks.length > 25){
        this.lastTenDrinks.shift()
        this.setLengthOfLastTenDrinks()
      }
    },
    getCommentsForCurrentDrink() {
      return this.currentComments = this.comments.filter(comment => comment.drink_id === this.currentRecipe.drink_id)
    }
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Averia+Serif+Libre|Montserrat');

#app-body {
  display: flex;
  flex-flow: row;
  justify-content: space-evenly;
  justify-content: center;
  align-items: center;
  line-height: 1.6;
  min-height: 80vh;
  max-width: 100vh;
  padding: 0 10rem 0 8rem;
  margin-left: 3rem;
}

/* main {
  display: flex;
  flex-direction: row;
} */

</style>

