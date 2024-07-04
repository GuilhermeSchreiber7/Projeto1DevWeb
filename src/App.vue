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
  Nascimento: '',
  Cidade:'',
  Estado: '',
  CEP: '',
  Hobbies: [],
  LinguagemProg:'',
  Biografia:''
 }) 

 const showprofile = ref(false)

 function mandarPerfil() {
  showprofile.value = true
 }

 function EsconderPerfil(){
  showprofile.value = false
 }
</script>

<template>
<div class="containerForm">
<main>
  <h1>Formulário:</h1>
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
        <label for="inputAge">Nascimento</label>
        <input id="inputAge" type="date" v-model.date="infos.Nascimento" placeholder="Digite sua Nascimento " required>
    </div>
        <div>
        <button type="submit">Enviar</button>
        </div>
    </form>

     <div v-show="showprofile">
    <p>Confirmação registro</p>
    <div>
        <p>Nome: {{ infos.Nome }}</p>
        <p>Nascimento: {{ infos.Nascimento }}</p>
        <p>Email: {{ infos.Email }}</p>
        <button @click="EsconderPerfil()">aaaaa</button>
    </div>
    </div>

</main>
</div>
</template>

<style scoped>

</style>
