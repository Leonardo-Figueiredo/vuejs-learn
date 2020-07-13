<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />

    <FormTodo v-on:add-todo="addComment" ></FormTodo>

    <div class="list-group">
      <p v-if="comments.length == 0" >Sem comentários...</p>
      <div class="list-group-item" v-bind:key="index" v-for="(comment, index) in allComments" >
        <span class="comment__author">
          Autor: <strong>{{ comment.name }}</strong>
        </span>
        <p>{{comment.comment}}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)" >Excluir</a>
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
  import FormTodo from './FormTodo';
  export default {
    components: {
      FormTodo,
    },
    data() {
        return {
          comments: [],
        }
      },
      methods: {
        addComment(comment) {
          this.comments.push(comment);
        },
        removeComment(index) {
          this.comments.splice(index, 1);
        }
      } ,
      computed: {
        allComments() {
          return this.comments.map(comment => ({
            ...comment,
            name: comment.name.trim() === '' ? 'Anônimo' : comment.name,
          }));
        }
      },
      watch: {
        comments(commentsValue) {
          console.log(commentsValue);
        }
      } 
  }
</script>