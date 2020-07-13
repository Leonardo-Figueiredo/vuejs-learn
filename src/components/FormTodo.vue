<template>
    <div class="form-todo form-group">
      <small>Deixe o nome em vazio e seu comentario será em anonimato.</small>
      <p>
        <input 
          type="text" 
          class="form-control" 
          name="author" 
          placeholder="Nome"
          v-model="name" >
      </p>

      <p>
        <textarea 
          name="comment" 
          class="form-control" 
          placeholder="Comentário"
          v-model="comment" >
        </textarea>
      </p>
      <button 
        type="submit" 
        class="btn btn-primary"
        v-on:click="addComment">
        Comentar
      </button>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        comment: '',
      }
    },
    methods: {
      addComment() {
          if (this.comment.trim() === '' ) {
           return alert('Comentário não pode ser vazio.');
          }

        this.$emit('add-todo', {
          name: this.name,
          comment: this.comment,
        });

         this.name = '';
         this.comment = '';    
      }
    }
  }
</script>
