<template>
    <div class="container">
      <div class="box">
        <div class="header">
          <p>Editar Livro</p>
        </div>
        <b-form @submit.prevent="editarLivro">
          <b-form-group label="ID do Livro" label-for="id">
            <b-form-input id="id" v-model.trim="idLivro" required class="input-smaller"></b-form-input>
          </b-form-group>
          <b-form-group label="Título" label-for="titulo">
            <b-form-input id="titulo" v-model.trim="titulo" required></b-form-input>
          </b-form-group>
          <b-form-group label="Autor" label-for="autor">
            <b-form-input id="autor" v-model.trim="autor" required></b-form-input>
          </b-form-group>
          <b-form-group label="Disponível" label-for="disponivel">
            <b-form-checkbox id="disponivel" v-model="disponivel" :checked="livro && livro.available"></b-form-checkbox>
          </b-form-group>
          <div class="buttons-container">
          <b-button type="submit" variant="primary">Editar Livro</b-button>
          <b-button id="back-to-home" variant="outline-primary" to="/">Início</b-button>
          </div>
      


        </b-form>

        <div v-if="!livro && !buscando && erro">
          <p>Nenhum livro encontrado com o ID {{ idLivro }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        idLivro: '',
        titulo: '',
        autor: '',
        disponivel: false,
        livro: null,
        buscando: false,
        erro: false,
      }
    },
    methods: {
      async editarLivro() {
        this.buscando = true;
        this.livro = null;
        this.erro = false;
  
        try {
          const response = await axios.put(`https://crude-bh.herokuapp.com/api/books/${this.idLivro}`, {
            title: this.titulo,
            author: this.autor,
            available: this.disponivel,
          }) .then((response) => {
                this.livro = response.data;
                this.$bvToast.toast('Livro editado com sucesso', {
                    title: 'Sucesso',
                    variant: 'success',
                    solid: true,
                });
                })
          this.livro = response.data;
        } catch (error) {
            console.error(error);
            this.erro = true;
            this.$bvToast.toast('Erro ao editar livro', {
                title: 'Erro',
                variant: 'danger',
                solid: true,
                });
                }
  
        this.buscando = false;
      },
    },
}
  

    </script>


<style scoped>
.container{
margin-bottom:15%;
box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
margin-top: 15%;
border-radius: 15px;
color: white;
padding: 10px;
border-radius: 25px;
margin:12% auto;
box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
padding: 20px;

}
.table td,
.table th {
color: white;
background-color: rgba(0, 0, 0, 0.3);

}



.buttons-container {
  display: flex;
 
  gap: 20px; /* Adjust the space between the buttons */
}



</style>