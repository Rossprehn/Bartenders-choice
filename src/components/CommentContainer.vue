<template>
  <section id='CommentContainer' v-if='!commentToggle && !donateToggle && !deleteToggle && !updateToggle'>
    <ul>
      <li v-for='comment in currentComments' :key='comment' :id='comment.id'>
        <h4>{{comment.name}}:</h4>
        <p>{{comment.comment}}</p>
      </li>
    </ul>
  </section>
</template>

<script>

export default {
  name: 'CommentContainer',
  props: ['currentComments', 'commentToggle', 'donateToggle', 'deleteToggle', 'updateToggle'],
  methods: {
    deleteComment () {
      if(!this.deleteToggle){
        console.log(this.deleteToggle)
        this.deleteToggle = true
      }

    }
  }
}
</script>

<style scoped>

#CommentContainer {
  margin: 30px 0;
  text-align: center;
}

ul {
  min-height: 15vh;
  width: 25rem;
  border-radius: 6px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.3);
  border: 1px solid darkgrey;
  text-align: left;
  margin: 30px 0;
  padding: 9px;
}
</style>
