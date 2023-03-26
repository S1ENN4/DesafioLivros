<template>
    <div class="all">
      <h2> Livros</h2>
      <table class="table table-striped">
        <thead>
          <tr>
            <th>ID</th>
            <th>Título</th>
            <th>Autor</th>
            <th>Disponível</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro._id }}</td>
            <td>{{ livro.title }}</td>
            <td>{{ livro.author }}</td>
            <td>{{ livro.available ? 'Sim' : 'Não' }}</td>
          </tr>
          <!-- Cria uma linha na tabela para cada objeto "livro" no array "livros" -->
          <!-- Define a propriedade "key" como "livro.id" para ajudar o Vue.js a identificar cada linha -->
          <!-- Exibe o título do livro na primeira coluna -->
          <!-- Exibe o autor do livro na segunda coluna -->
          <!-- Exibe "Sim" ou "Não" na terceira coluna, dependendo do valor da propriedade "available" do objeto "livro" -->
        </tbody>
      </table>
      <b-button id="back-to-home" variant="outline-primary" to="/">Início</b-button>
      


    </div>
  </template>
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        livros: [],
      }
    },
    async created() {
      try {
        const response = await axios.get('https://crude-bh.herokuapp.com/api/books');
        this.livros = response.data;
        // Faz uma requisição GET para a API de livros
        // Atribui o array de objetos "livro" 
      } catch (error) {
        console.error(error);
      }
    },
  }
  </script>

  <style scoped>
  .all{
  margin-bottom:15%;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
  margin-top: 15%;
  border-radius: 15px;
  color: white;
  padding: 10px;
  border-radius: 25px;
  margin:12% auto;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
  
}
.table td,
.table th {
  color: white;
  background-color: rgba(0, 0, 0, 0.3);

}
</style>