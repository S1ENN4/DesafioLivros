<template>
  <div id="app">
    <b-container>
      <div class="container">
        <NavigationBar/>
  
      </div>

      <HomeScreen/>
      
      <router-view></router-view>
      <!-- This is where the components specified in the routes array will be rendered -->
    </b-container>
    <DownFooter/>
  </div>
</template>

<script>
import Vue from 'vue'
import VueRouter from 'vue-router'
import HomeScreen from './components/HomeScreen.vue'
import CadastrarLivro from './components/CadastrarLivro.vue'
import ListarLivro from './components/ListarLivro.vue'
import NavigationBar from './components/NavigationBar.vue'
import DownFooter from './components/DownFooter.vue'
import DeletarLivro from './components/DeletarLivro.vue'
import ListarID from './components/ListarID.vue'
import ListarDisponiveis from './components/ListarDisponiveis.vue'
import EditarLivro from './components/EditarLivro.vue'
import DeletarTodos from './components/DeletarTodos.vue'



Vue.use(VueRouter)

const routes = [
  {
    path: '/',
    name: 'HomeScreen',
    component: HomeScreen
  },
  {
    path: '/cadastrar-livro',
    name: 'CadastrarLivro',
    component: CadastrarLivro
  },
  {
    path: '/listar-livros',
    name: 'ListarLivro',
    component: ListarLivro
  },
  {
    path: '/deletar-livros',
    name: 'DeletarLivro',
    component: DeletarLivro
  },
  {
    path: '/listar-id',
    name: 'ListarID',
    component: ListarID
  },
  {
    path: '/listar-disponiveis',
    name: 'ListarDisponiveis',
    component: ListarDisponiveis
  },
  {
    path: '/editar-livro',
    name: 'EditarLivro',
    component: EditarLivro
  },
  {
    path: '/deletar-todos',
    name: 'DeletarTodos',
    component: DeletarTodos
  }
  
]

const router = new VueRouter({
  mode: 'history',
  base: process.env.BASE_URL,
  routes
})

export default {
  router,
  components: {
    NavigationBar,
    DownFooter,

    
  }
}
</script>

<style>

  .image {
    position:absolute;
    width: 30%;
    top: 15%;
    right:10px;
  }




body {
    background-image: url('./assets/3418448.jpg');
    background-repeat: no-repeat;
    background-size: cover;
  }


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
  margin-top: 60px;
}
</style>