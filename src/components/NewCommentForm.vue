<template>
  <div id='NewCommentForm' v-if='commentToggle'>
    <form id='comment-input' v-on:submit.prevent='postComment'>
        <label id='commenters-name'>Commenter's Name: </label>
        <input v-model='commentObject.name' type='text' id='name' />
        <label>Comment: </label>
        <textarea v-model='commentObject.comment' id='new-comment'  rows='8' cols='100'></textarea>
        <div class='buttons'>
          <input id='submit' type='submit' value='Submit' />
          <button v-on:click='showAddCommentComponent' type='button' name='cancel'>Cancel</button>
        </div>
      </form>
  </div>
</template>
<script>

export default {
  name: 'NewCommentForm',
  props: ['commentToggle', 'apiURL', 'drinkRecipe', 'getComments', 'showAddCommentComponent'],
  data() {
    return {
      commentObject: {
        'name': '',
        'comment': '',
        'drink_id': undefined
      }
    }
  },
  methods: {
    postComment() {
      this.commentObject.drink_id = this.drinkRecipe.drink_id
      if(event.target.name.value.length > 0 && event.target['new-comment'].value.length > 0) {
        fetch(this.apiURL + 'comments', {
          method: 'POST',
          headers: new Headers({ 'Content-Type': 'application/json' }),
          body: JSON.stringify(this.commentObject)
        })
          .then(res => res.json())
          .then(json => {
            this.getComments()
            this.showAddCommentComponent()
          })
      } else {
        console.log('please finish filling out the comment card')
      }
      this.commentObject.name = ''
      this.commentObject.comment = ''
      this.commentObject.drink_id = undefined
    }
  }
}
</script>

<style scoped>

#NewCommentForm {
  margin: 20px 0 30px 0;
  width: 71vmin;
  font-family: 'Montserrat', sans-serif;
}

form {
  display: flex;
  flex-flow: column;
  align-items: center;
}

label {
  margin: 10px 0;
}

input {
  border: solid black 1px;
  border-radius: 5px;
  outline: none !important;
  width: 70vmin;
  font-size: 1rem;
  font-family: 'Montserrat', sans-serif;
}

textarea {
  border-radius: 5px;
  outline: none !important;
  width: 70vmin;
  font-size: 1rem !important;
  font-family: 'Montserrat', sans-serif;
}

#commenters-name{
  float: left;
}

.buttons {
  margin: 10px 0;
}

#submit {
  background-color: rgb(109, 194, 118);
  border-color: rgb(109, 194, 118);
  border-radius: 5px;
  width: 150px;
  height: 50px;
  outline: none !important;
  font-size: 1rem;
  font-family: 'Montserrat', sans-serif;
}

#submit:hover {
  background-color: rgb(80, 215, 93);
  cursor: pointer;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

button {
  width: 150px;
  height: 50px;
  background-color: rgb(233, 207, 114);
  border-color: rgb(233, 207, 114);
  border-radius: 5px;
  margin: 5px;
  outline: none !important;
  font-size: 1rem;
  font-family: 'Montserrat', sans-serif;
}

button:hover {
  background-color: rgb(242, 229, 59);
  cursor: pointer;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

@media screen and (max-width: 686px) {
  #NewCommentForm {
    width: 80vmin;
  }

  input {
    width: 80vmin;
  }

  textarea {
    width: 80vmin;
  }

  button {
    width: 30vmin;
  }

  #submit {
    width: 30vmin;
  }
}
</style>