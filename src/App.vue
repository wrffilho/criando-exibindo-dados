/*1. Para que serve o atributo data de um componente?
 É um método  que contem todos atributos de um componente, esse  metodo retorna todas as variáveis
 que usaremos  no componente.
2. O que são diretivas? 
São manipuladoras de template, podendo alterar o DOM acrescentando ou omitindo informações e elementos.
 Defina cada diretiva a seguir:
v-once ->  não permite alteração, desativa a reatividade  
v-if -> condicional
v-text -> usado para mostrar o valor de um atributo e a interpolação do Mustache
v-for -> usado para percorrer itens de uma lista por exemplo
v-model -> pegar dados digitados pelo usuário, vincula o valor do elemento com uma variável no seu código
v-on (@) -> para invocar eventos
v-bind (:) - > mapeia e altera atributos html */


<template>
  <div id="app">
    <h1 v-text="msg"></h1>
    <h2 v-text="titulo"></h2>
    <h3 v-text="subtitulo"></h3>
    <h4 v-text="nome"></h4>
    <small  v-once v-text="nome"></small><br><br>
    <h5>Aqui-{{nome}}</h5>
    <div v-if="tarefas.length <= 0">Não há tarefas</div>
    <div v-if="tarefas.length > 0">Existem {{tarefas.length}} tarefas
      <ul>
        <li v-for="tarefa in tarefas"> {{ tarefa }} </li>
      </ul>
    </div>
    <input v-model="subtitulo" :disabled="tarefas.length == 0" type="text" placeholder="Descrição">
    <button @click="tarefas = []" :disabled="tarefas.length == 0">Limpar</button>
    <button @click="mostra = !mostra" :disabled="nome != 'MINEIRÃO'" >Trocar</button>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Aprendendo Vue js',
      titulo: 'Listagem de tarefas',
      subtitulo: 'Defina uma descrição',
      tarefas: [],
      nome: "Mané Garrincha",
      mostra: true,
      nBotao: "Recarregar"
    }
  },
  mounted() {
    setTimeout( () => {
      this.titulo = "Novo título",
      this.tarefas = ['tarefa 1', 'tarefa 2', 'tarefa 3', 'tarefa 4']}, 3000 ),

      setTimeout(() => {
      this.nome = "MINEIRÃO"}, 4000)
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: bold;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
