<template>
    <div required class="delete">
      <h2>Deletar Livro</h2>
      <b-form @submit.prevent="deletarLivro">
        <b-form-group label="ID do Livro" label-for="id">
          <b-form-input id="id" v-model.trim="idLivro" ></b-form-input>
        </b-form-group>


        <div class="buttons-container">
        <b-button type="submit" variant="danger" :disabled="!formularioValido">
          Deletar Livro
        </b-button>
 
        <b-button id="back-to-home" variant="outline-primary" to="/">Início</b-button>
        </div>
      </b-form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        idLivro: '',
      }
    },
    computed: {
      formularioValido() {
        return this.idLivro.trim().length > 0;
      },
    },
    methods: {
      async deletarLivro() {
        if (this.formularioValido) {
          try {
            await axios.delete(`https://crude-bh.herokuapp.com/api/books/${this.idLivro}`);
  
            this.$bvToast.toast('Livro deletado com sucesso!', {
              title: 'Sucesso',
              variant: 'success',
              solid: true,
            });
  
            this.idLivro = '';
          } catch (error) {
            console.error(error);
            this.$bvToast.toast('Erro ao deletar o livro.', {
              title: 'Erro',
              variant: 'danger',
              solid: true,
            });
          }
        }
      },
    },
  }
  </script>
  
  <style scoped>
  .delete{
  width: 40%;
  padding: 20px;
  color: white;
  border-radius: 25px;
  margin:12% auto;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
}

*{
  font-family: Arial, Helvetica, Sans-serif;
}



.buttons-container {
  display: flex;
  justify-content: center;
  gap: 20px; /* Adjust the space between the buttons */
}





  </style>
  