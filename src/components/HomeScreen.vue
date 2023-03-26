<template>
  <div class="container">
    <div class="parent-container">
    <div class="apresentation">
      <h2>Painel Administrativo</h2>
     
    </div>

    </div>
    
    <div class="box">
      <div class="header">
        
      </div>
      
      <ul class="button-list">
       
        <li>
          <b-button v-b-tooltip.hover.righttop title="Cadastra um novo livro" class="button-green" variant="outline-light" @click="$router.push('/cadastrar-livro') ">Cadastrar Livro</b-button>
        </li>
        <li>
          <b-button v-b-tooltip.hover.righttop title="Exibe uma lista com todos os livros cadastrados"  class="button-spacing" variant="outline-light" @click="$router.push('/listar-livros')">Listar Todos os Livros</b-button>
        </li>
        <li>
          <b-button v-b-tooltip.hover.righttop title="Deleta um livro (Necessário ter o ID)" class="button-delete" variant="outline-light" @click="$router.push('/deletar-livros')">Deletar Livro</b-button>
        </li>
        <li>
          <b-button v-b-tooltip.hover.righttop title="Exibe detalhes de um livro (Necessário ter o ID)" class="button-delete" variant="outline-light" @click="$router.push('/listar-id')">Detalhar Livro</b-button>
        </li>
        <li>
          <b-button v-b-tooltip.hover.righttop title="Exibe apenas os livros disponíveis para compra" class="button-delete" variant="outline-light" @click="$router.push('/listar-disponiveis')">Verificar Livros Disponiveis</b-button>
        </li>
        <li>
          <b-button v-b-tooltip.hover.righttop title="Edita um livro (Necessita de ID), é possível editar o status, titulo e autor." class="button-delete" variant="outline-light" @click="$router.push('/editar-livro')">Editar Livro/Status</b-button>
        </li>
        <li>
          <b-button v-b-tooltip.hover.righttop title="Deleta TODOS os livros do sistema" class="button-deleteall" variant="outline-light" @click="$router.push('/deletar-todos')">Deletar Todos os Livros</b-button>
        </li>
      </ul>
      
    </div>
  </div>
</template>

<style scoped>
* {
  font-family: 'Open Sans', sans-serif;
}

.box {
  max-width: 38%;
  height: 30%;
  margin: 1% auto;
  margin-bottom: 20px;
  width: 100%;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
  display: flex;
  justify-content: center;
  align-items: center;
}

.header {
  color: aliceblue;
  font-family: 'Open Sans', sans-serif;
  margin-bottom: 20px;
}

.header h1 {
  font-size: 36px;
  margin-bottom: 10px;
}

.header p {
  font-size: 18px;
  margin-bottom: 0;
}
button{
  width: 100% ;
}

.button-list {
  color: white;
  justify-content: center;
  list-style: none;
  margin: 0;
  padding: 0;
  flex-direction: column;
  align-items: center;
}

.button-list li {
  margin-bottom: 10px;
}

.button-spacing {
  margin-right: 10px;
}



.parent-container {
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center;     /* Center vertically */
  
}

.apresentation{
  position:static;
  margin-top: 20px;
  color: white;
  max-width: 35%;
  height: 30%;

 justify-content: center;
  margin-bottom: 20px;
  width: 100%;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.9);
  text-align: center;
  
}
.button-deleteall:hover{
  background-color: red;
  
}

</style>
