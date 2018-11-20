<template>
  <div id='DrinkCard'>
    <div id='info'>
    <h3>Ingredients:</h3>
    <p id='ingredients'>{{recipe.ingredients}}</p>
    <h3>Instructions:</h3>
    <p id='recipe-description'>{{recipe.recipe}}</p>
    </div>
    <div id='center'>
      <h2>{{recipe.name}}</h2>
      <img :src='recipe.image' alt='please wait for server load' />
    </div>
  </div>
</template>

<script>
export default {
  name: 'DrinkCard',
  data: () => ({
  }),
  props: ['recipe']
}</script>

<style scoped>
  #DrinkCard {
    display: flex;
    flex-flow: row;
    align-items: center;
    background-color: white;
    padding: 2vmin;
    border-radius: 5px;
  }
  #ingredients {
    font-style: italic;
  }
  #center {
    text-align: center;
    margin: .7rem
  }
  #info{
    margin: .7rem;
  }
  img {
    max-width: 70vmin;
    max-height: 60vmin;
    border-radius: 5px;
    margin: .35rem;
  }
  h2 {
    font-weight: 400;
    font-size: 2rem;
    line-height: 1;
    font-family: 'Averia Serif Libre', cursive;
  }
  h3{
    font-weight: 200;
    font-size: 1.25rem;
    padding-top: .4rem; 
  }
  p {
    font-size: 1rem;
    width: 70vmin;
    font-family: 'Montserrat', sans-serif;
    font-weight: 100;
  }
</style>
