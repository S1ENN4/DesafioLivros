<template>
    <div class="container">
      <div class="box">
        <div class="header">
          <p>Excluir Todos os Livros</p>
        </div>

        <div class="buttons-container">
        <b-button variant="danger" @click="excluirTodos">Excluir Todos</b-button>
        <b-button id="back-to-home" variant="outline-primary" to="/">Início</b-button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    methods: {
      async excluirTodos() {
        const confirmation = window.prompt("Digite 'confirmar' para excluir todos os livros:");
  
        if (confirmation === 'confirmar') {
          try {
            await axios.delete('https://crude-bh.herokuapp.com/api/books');
            alert('Todos os livros foram excluídos com sucesso!');
          } catch (error) {
            console.error(error);
          }
        } else {
          alert('A exclusão foi cancelada pelo usuário.');
        }
      },
    },
  };
  </script>
  
  <style scoped>
.container {
  max-width: 30%;
  height: 30%;
  margin: 15% auto;
  border: 1px solid black;
  width: 100%;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
  justify-content: center;
  align-items: center;
  margin-bottom: 205px;
}

.header {
  color: aliceblue;
  font-family: 'Open Sans', sans-serif;
  margin-bottom: 20px;
}

.header p {
  font-size: 18px;
  margin-bottom: 0;
}

.content {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.buttons-container {
  display: flex;
  justify-content: center;
  gap: 20px; /* Adjust the space between the buttons */
}

</style>