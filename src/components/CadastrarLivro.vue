<template>
  <div>
    <!-- Formulário para cadastro de livro -->
    <div class="form-container">
      <b-form @submit.prevent="cadastrarLivro" required class="main">
        <b-form-group label="Título do Livro" label-for="titulo">
          <b-form-input id="titulo" v-model.trim="livro.title" :state="tituloValido" @input="validarTitulo" required class="input-smaller"></b-form-input>
        </b-form-group>

         <!-- vincula o valor do campo de entrada de texto ao objeto 'livro' -->
         <!-- controla o estado de validação do campo de entrada de texto -->
         <!-- chama o método de validação do título quando o valor do campo é alterado -->
         <!-- indica que o campo é obrigatório -->

        <b-form-group label="Autor do Livro" label-for="autor">
          <b-form-input id="autor" v-model.trim="livro.author" :state="autorValido" @input="validarAutor" required class="input-smaller"></b-form-input>
        </b-form-group>

         <!-- vincula o valor do campo de entrada de texto ao objeto 'livro' -->
         <!-- controla o estado de validação do campo de entrada de texto -->
         <!-- chama o método de validação quando o valor do campo é alterado -->
         <!-- indica que o campo é obrigatório -->

        
        


        <b-tooltip target="disp" title="Marque essa caixa se o livro estiver disponível"> </b-tooltip>


          <b-form-group id ="disp">
          <b-form-checkbox id="disponibilidade" v-model="livro.available">
            Disponível
          </b-form-checkbox>
        </b-form-group>


              
       

        <div class="buttons-container">
        <b-button type="submit" variant="primary" :disabled="!formularioValido">
          Cadastrar Livro
        </b-button>
        
        <b-button id="back-to-home" variant="outline-primary" to="/">Início</b-button>
      </div>
      </b-form>
    </div>
  </div>
</template>

<style>
.main {
  max-width: 800px; /* Define a largura máxima do formulário */
  margin: 0 auto; /* Centraliza o formulário horizontalmente */
  padding: 20px; /* Adiciona um espaçamento interno de 20 pixels */
}

.form-container {
  display: flex;
  justify-content: center;
}

.input-smaller {
  max-width: 300px;
}
</style>

<script>
export default {
  data() {
    return {
      livro: {  // objeto que armazena as informações do livro
        title: '',  // título do livro
        author: '',  // autor do livro
        available: false,  // disponibilidade do livro
      },
      tituloValido: null,  // estado de validação do título
      autorValido: null,  // estado de validação do autor
    }
  },
  computed: {
    formularioValido() {
      return this.tituloValido && this.autorValido  // retorna verdadeiro se ambos os campos são válidos
    },
  },
  methods: {
    validarTitulo() {  // valida o campo de entrada de texto para o título
      this.tituloValido = this.livro.title.length >= 3 && this.livro.title.length <= 60  // atualiza o estado de validação do título
    },
    validarAutor() {  // valida o campo de entrada de texto para o autor
      const regex = /^[a-zA-Z\s]+$/;  // expressão regular para validar somente letras e espaços em branco
      this.autorValido =
        this.livro.author.length >= 3 &&  // o autor deve ter pelo menos 3 caracteres
        this.livro.author.length <= 60 &&  // o autor não deve ter mais de 60 caracteres
        regex.test(this.livro.author)  // o autor deve conter apenas letras e espaços em branco
    },
    async cadastrarLivro() {  // método para enviar a requisição POST para cadastrar o livro
      if (this.formularioValido) {  // verifica se o formulário é válido
        try {
      // envia a requisição POST para a API
      const response = await this.$axios.post('https://crude-bh.herokuapp.com/api/books', this.livro)

      // emite um evento informando que o livro foi cadastrado
      this.$emit('livroCadastrado', response.data)

      // limpa os campos do formulário
      this.livro = {
        title: '',
        author: '',
        available: false,
      }

      // reseta o estado de validação dos campos de entrada de texto
      this.tituloValido = null
      this.autorValido = null

      // exibe uma mensagem de sucesso
      this.$bvToast.toast('Livro cadastrado com sucesso!', {
        title: 'Sucesso',
        variant: 'success',
        solid: true,
      })
    } catch (error) {
      // exibe uma mensagem de erro em caso de falha na requisição
      this.$bvToast.toast('Erro ao cadastrar o livro.', {
        title: 'Erro',
        variant: 'danger',
        solid: true,
      })
    }
  }
},
},
}
</script>


<style scoped>
.form-container{
  width: 40%;
 
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