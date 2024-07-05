<script setup>
import { ref } from 'vue'

const Estados = [
  { uf: 'AC', nome: 'Acre' },
  { uf: 'AL', nome: 'Alagoas' },
  { uf: 'AP', nome: 'Amapá' },
  { uf: 'AM', nome: 'Amazonas' },
  { uf: 'BA', nome: 'Bahia' },
  { uf: 'CE', nome: 'Ceará' },
  { uf: 'DF', nome: 'Distrito Federal' },
  { uf: 'ES', nome: 'Espírito Santo' },
  { uf: 'GO', nome: 'Goiás' },
  { uf: 'MA', nome: 'Maranhão' },
  { uf: 'MT', nome: 'Mato Grosso' },
  { uf: 'MS', nome: 'Mato Grosso do Sul' },
  { uf: 'MG', nome: 'Minas Gerais' },
  { uf: 'PA', nome: 'Pará' },
  { uf: 'PB', nome: 'Paraíba' },
  { uf: 'PR', nome: 'Paraná' },
  { uf: 'PE', nome: 'Pernambuco' },
  { uf: 'PI', nome: 'Piauí' },
  { uf: 'RJ', nome: 'Rio de Janeiro' },
  { uf: 'RN', nome: 'Rio Grande do Norte' },
  { uf: 'RS', nome: 'Rio Grande do Sul' },
  { uf: 'RO', nome: 'Rondônia' },
  { uf: 'RR', nome: 'Roraima' },
  { uf: 'SC', nome: 'Santa Catarina' },
  { uf: 'SP', nome: 'São Paulo' },
  { uf: 'SE', nome: 'Sergipe' },
  { uf: 'TO', nome: 'Tocantins' }
]
 const infos = ref({
  Nome: '',
  Email: '',
  Senha: '',
  ConfSenha: '',
  Nascimento: '',
  Cidade:'',
  Estado: '',
  CEP: '',
  Hobbies: [],
  LinguagemProg:'',
  Biografia:''
 }) 

 const showprofile = ref(false)
 const form = ref(true)

 function mandarPerfil() {
  showprofile.value = true
  form.value = false
 }

 function EsconderPerfil(){
  showprofile.value = false
  form.value = true
 }
</script>

<template>
<div>
<main>
<div class="containerForm" v-show="form">
  <h1>SUAS INFORMAÇÕES</h1>
  <form @submit.prevent="mandarPerfil()">
    <div>
        <label for="inputName">Nome</label>
        <input type="text" v-model.trim="infos.Nome" placeholder="Digite seu nome" id="inputName" required />
    </div>
    <div>
        <label for="inputEmail">Email</label>
        <input id="inputEmail" type="email" v-model.trim="infos.Email" placeholder="Digite seu email" required>
    </div>
    <div>
        <label for="inputSenha">Senha</label>
        <input id="inputSenha" type="password" v-model.trim="infos.Senha" placeholder="Digite sua Senha" required>
    </div>
    <div>
        <label for="inputConfSenha">Confirmação de Senha</label>
        <input id="inputConfSenha" type="password" v-model.trim="infos.ConfSenha" placeholder="Confirme sua Senha" required>
    </div>
    <div>
        <label for="inputAge">Nascimento</label>
        <input id="inputAge" type="date" v-model.date="infos.Nascimento" placeholder="Digite sua Nascimento " required>
    </div>
    <div>
        <label for="inputCEP">CEP</label>
        <input id="inputCEP" type="text" v-model="infos.CEP" placeholder="Digite seu CEP" required>
    </div>
    <div>
        <label for="inputCEP">Cidade</label>
        <input id="inputCEP" type="text" v-model="infos.Cidade" placeholder="Digite sua Cidade" required>
    </div>
    <div>
        <label for="inputEstado">Estado</label>
      
            <select id="inputEstado" value="Estado" v-model="infos.Estado">
              <option v-for="Estado of Estados" :key="Estado.uf" :value="Estado.uf">
                {{ Estado.nome }}
            </option>
            </select>
    </div>
        <div>
            <p>Hobbies:</p>
            <input type="checkbox" id="hobbies" value="Esporte" v-model="infos.Hobbies">
            <label for="hobbies">Esportes</label>

            <input type="checkbox" id="hobbies" value="Viagens" v-model="infos.Hobbies">
            <label for="hobbies">Viagens</label>

            <input type="checkbox" id="hobbies" value="Música" v-model="infos.Hobbies">
            <label for="hobbies">Músicas</label>

            <input type="checkbox" id="hobbies" value="Leitura" v-model="infos.Hobbies">
            <label for="hobbies">Leitura</label>

            <input type="checkbox" id="hobbies" value="VIdeoGame" v-model="infos.Hobbies">
            <label for="hobbies">Video Game</label>
        </div>
        <div>
            <p>Linguagem preferida:</p>
            <input type="radio" id="Js" value="JavaScript" v-model="infos.LinguagemProg">
            <label for="Js">JavaScript</label>

            <input type="radio" id="Java" value="Java" v-model="infos.LinguagemProg">
            <label for="Java">Java</label>

            <input type="radio" id="C" value="C" v-model="infos.LinguagemProg">
            <label for="C">C</label>

            <input type="radio" id="Py" value="Python" v-model="infos.LinguagemProg">
            <label for="Py">Python</label>

            <input type="radio" id="C#" value="C#" v-model="infos.LinguagemProg">
            <label for="C#">C#</label>
        </div>
         <div>
          <label for="bio">Biografia</label>
          <input type="text" id="bio" placeholder="Sua Biografia (opcional)" v-model="infos.Biografia">
         </div>

        <div>
        <button v-if="infos.Senha == infos.ConfSenha && infos.Senha.length >= 8" type="submit">Enviar</button>
        </div>
    </form>
  </div>

     <div id="infosEnviadas" v-show="showprofile" >
      <h1>SEUS DADOS</h1>
        <p>Nome: {{ infos.Nome }}</p>
        <p>Nascimento: {{ infos.Nascimento }}</p>
        <p>Email: {{ infos.Email }}</p>
        <p>Cidade: {{ infos.Cidade }}</p>
        <p>Estado: {{ infos.Estado }}</p>
        <p>Hobbies: {{ infos.Hobbies.join(', ') }}</p>
        <p>Linguagem Preferida: {{ infos.LinguagemProg }}</p>
        <div class="Bio"><p> Biografia: {{ infos.Biografia }}</p></div>
        <button @click="EsconderPerfil()">Voltar</button>
    </div>

</main>
</div>
</template>

<style scoped>

</style>
