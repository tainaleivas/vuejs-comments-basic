<template>
<div class="form-todo form-group">
  <p>
    <input placeholder="nome" type="text" name="author" class="form-control" v-model="name" />
  </p>
  <p>
    <textarea placeholder="comentário" type="text" name="author" class="form-control" v-model="message" textarea/>
  </p>
    <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
</div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        message: ''
      }
    },
    methods: {
      addComment() {
          // validação caso o campo comentário esteja vazio ele não é adicionado
          // trim -> apaga os espaçoso em branco antes e depois
          if (this.message.trim() === '') {
            return;
          }

          this.$emit('add-todo', {
            name: this.name,
            message: this.message,
          });     

          // apagar os campos depois de usar
          this.name = '';
          this.message = '';
        }
    }
  }
</script>