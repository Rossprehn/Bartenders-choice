<template>
  <div id='Header'>
    <p>Best place for daily new cocktail resipies</p>
  </div>
</template>
<script>
export default {
  name: 'Header'
}
</script>
<style scoped>
  #Header {
    display: flex;
    flex-flow: row;
    justify-content: space-between;
    width: 100vw;
    height: 12vh;
  }
  p {
    font-family: 'Montserrat', sans-serif;
    padding-bottom: 3vh;
  }
</style>
