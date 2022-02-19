<template>
  <div class="about">
    <div class="wrap-tabs">
    <ul>
      <li @click="switchTab(0)">Tab 1</li>
      <li @click="switchTab(1)">Tab 2</li>
      <li @click="switchTab(2)">Tab 3</li>
      <li @click="switchTab(3)">Tab 4</li>
    </ul>
    <div class="content" v-if="user.nome !== ''">
      <div v-if="tab === 0 && load === false">
        <div>
          <label for="">Nome</label><br>          
          <input type="text" v-model="user.nome">
        </div>
        <div>
          <label for="">SobreNome</label><br>          
          <input type="text" v-model="user.sobrenome">
        </div>
        <div>
          <label for="">Idade</label><br>          
          <input type="text" v-model="user.idade">
        </div>
        <div>
          <label for="">Sexo</label><br>          
          <input type="text" v-model="user.sexo">
        </div>
        <div>
          <label for="">Profissão</label><br>          
          <input type="text" v-model="user.profissao">
        </div>
      </div>
      <div v-if="tab === 1 && load === false">
        <div>
          <strong>Nome:</strong>{{user.nome}} <br>
          <strong>SobreNome:</strong>{{user.sobrenome}} <br>
          <strong>Idade:</strong>{{user.idade}} <br>
          <strong>Sexo:</strong>{{user.sexo}} <br>
          <strong>Profissão:</strong>{{user.profissao}} <br>
        </div>
      </div>
      <div v-if="tab === 2 && load === false">
        <div>
          <strong>Nome:</strong>{{user.nome}} <br>
          <strong>SobreNome:</strong>{{user.sobrenome}} <br>
          <strong>Idade:</strong>{{user.idade}} <br>
          <strong>Sexo:</strong>{{user.sexo}} <br>
          <strong>Profissão:</strong>{{user.profissao}} <br>
        </div>
      </div>
      <div v-if="tab === 3 && load === false">
        <div>
          <strong>Nome:</strong>{{user.nome}} <br>
          <strong>SobreNome:</strong>{{user.sobrenome}} <br>
          <strong>Idade:</strong>{{user.idade}} <br>
          <strong>Sexo:</strong>{{user.sexo}} <br>
          <strong>Profissão:</strong>{{user.profissao}} <br>
        </div>
      </div>
    </div>
    </div>
    <div class="mask" v-if="load">
      <div class="loader"></div>
    </div>
  </div>
</template>
<script>
const examples = [
  {nome: 'Yan', sobrenome: 'Felipe',idade: '30', sexo: 'Duvidoso', profissao: 'Garoto de programa com a parte de tras'},
  {nome: 'Leandro', sobrenome: 'Ulisses',idade: '34', sexo: 'Sei não ein', profissao: 'Garoto de programa com a parte de tras'},
  {nome: 'Juliano', sobrenome: 'Terraboi',idade: '40', sexo: 'Baitola', profissao: 'Garoto de programa com a parte de tras'},
  {nome: 'Caio', sobrenome: 'Passarelli',idade: '32', sexo: 'Másculo', profissao: 'Garoto de programa com a parte da frente'},
]
  export default {
    name: 'about',
    data() {
      return {
        tab: 1,
        load: false,
        user: {nome: '', sobrenome: '', idade: 0, sexo: '', profissao: ''}
      }
    },
    methods: {
      getApiValue(value) {
        return new Promise((resolve, reject) => {
          setTimeout(() => {
            resolve(examples[value])
          }, 3000);
        })  
      },
      async setVarValue(tabNumber) {
        this.load = true
        this.user = await this.getApiValue(tabNumber)
        this.load = false
      },
      switchTab(tabNumber) {
        this.setVarValue(tabNumber)
        this.tab = tabNumber
      }
    }
  }
</script>
<style>
  .about {
    width: 100% ;
    min-height: 100vh;
    border: 1px solid #ff0; 
  }
  ul, li{
    list-style: none;
  }
  ul {
    width: fit-content;
    display: flex;
    border: 1px solid #f00;
  }
  li {
    padding: 5px 10px;
    cursor: pointer;
  }
  li:hover {
    background-color: #ccc;
  }
  .mask {
    width: 100vw;
    height: 100vh;
    background: #00000055;
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .loader {
    width: 100px;
    height: 100px;
    border-right: 1px solid #ff0;
    border-bottom: 2px solid #ff0;
    border-left: 3px solid #ff0;
    border-top: 4px solid #ff0;
    border-radius: 50px;
    animation: spin 1s linear infinite;
  }
  input[type="text"]{
    border: 1px solid #ccc;
    padding: 5px 7px;
  }
  
@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
