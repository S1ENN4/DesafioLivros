<template>
    <div class="pesquisar">
      <h2>Buscar Livro</h2>
      <b-form @submit.prevent="buscarLivro">
        <b-form-group label="ID do Livro" label-for="id">
          <b-form-input id="id" v-model.trim="idLivro" required class="input-smaller"></b-form-input>
        </b-form-group>

        <div class="buttons-container">
        <b-button type="submit" variant="primary">Buscar</b-button>
          
        <b-button id="back-to-home" variant="outline-primary" to="/">Início</b-button>
        </div>

      </b-form>
  
      <div  class="result" v-if="livro">
        <h3>{{ livro.title }}</h3>
        <p><strong>Autor:</strong> {{ livro.author }}</p>
        <p><strong>Disponível:</strong> {{ livro.available ? 'Sim' : 'Não' }}</p>
        <p><strong>Criado em:</strong> {{ livro.createdAt }}</p>
        <p><strong>Atualizado em:</strong> {{ livro.updatedAt }}</p>
      </div>
  
      <div v-if="!livro && buscando">
        <p>Buscando livro...</p>
      </div>
  
      <div v-if="!livro && !buscando && erro">
        <p>Nenhum livro encontrado com o ID {{ idLivro }}</p>
      </div>
  
     
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        idLivro: '',
        livro: null,
        buscando: false,
        erro: false,
      }
    },
    methods: {
      async buscarLivro() {
        this.buscando = true;
        this.livro = null;
        this.erro = false;
  
        try {
          const response = await axios.get(`https://crude-bh.herokuapp.com/api/books/${this.idLivro}`);
          this.livro = response.data;
        } catch (error) {
          console.error(error);
          this.erro = true;
        }
  
        this.buscando = false;
      },
    },
  }
  </script>
  
  <style scoped>
  .pesquisar{
  padding-bottom: 500px;
  width: 40%;
  padding: 20px;
  color: white;
  border-radius: 25px;
  margin:12% auto;
  margin-bottom: 300px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
}

.result{
    border-radius: 25px;
    margin:12% auto;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
    padding: 10%;
    background-color: white;
    color:black;
}



.buttons-container {
  display: flex;
  
  gap: 20px; /* Adjust the space between the buttons */
}






  </style>
  