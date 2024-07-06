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
    Cidade: '',
    Estado: '',
    CEP: '',
    Hobbies: [],
    LinguagemProg: '',
    Biografia: ''
})

const showprofile = ref(false)
const form = ref(true)

function mandarPerfil() {
    showprofile.value = true
    form.value = false
}

function EsconderPerfil() {
    showprofile.value = false
    form.value = true
}
</script>

<template>

    <body>
        <div>
            <main>
                <div class="containerForm" v-show="form">
                    <h1>SUAS INFORMAÇÕES</h1>
                    <form @submit.prevent="mandarPerfil()">
                        <div class="InputLabel">
                            <label for="inputName">Nome</label>
                            <input type="text" v-model.trim="infos.Nome" placeholder="Digite seu nome" id="inputName"
                                required />
                        </div>
                        <div class="InputLabel">
                            <label for="inputEmail">Email</label>
                            <input id="inputEmail" type="email" v-model.trim="infos.Email"
                                placeholder="Digite seu email" required>
                        </div>
                        <div class="InputLabel">
                            <label for="inputSenha">Senha (min. 8 caracteres)</label>
                            <input id="inputSenha" type="password" v-model.trim="infos.Senha"
                                placeholder="Digite sua Senha" required>
                        </div>
                        <div class="InputLabel">
                            <label for="inputConfSenha">Confirmação de Senha</label>
                            <input id="inputConfSenha" type="password" v-model.trim="infos.ConfSenha"
                                placeholder="Confirme sua Senha" required>
                        </div>
                        <div class="InputLabel">
                            <label for="inputAge">Nascimento</label>
                            <input id="inputAge" type="date" v-model.date="infos.Nascimento"
                                placeholder="Digite sua Nascimento " required>
                        </div>
                        <div class="InputLabel">
                            <label for="inputCEP">CEP</label>
                            <input id="inputCEP" type="number" v-model="infos.CEP" placeholder="Digite seu CEP"
                                required>
                        </div>
                        <div class="InputLabel">
                            <label for="inputCEP">Cidade</label>
                            <input id="inputCEP" type="text" v-model="infos.Cidade" placeholder="Digite sua Cidade"
                                required>
                        </div>
                        <div class="InputLabel">
                            <label for="inputEstado">Estado</label>

                            <select id="inputEstado" value="Estado" v-model="infos.Estado" required>
                                <option v-for="Estado of Estados" :key="Estado.uf" :value="Estado.uf">
                                    {{ Estado.nome }}
                                </option>
                            </select>
                        </div>
                        <div>
                            <p class="titulo">Hobbies:</p>
                            <input type="checkbox" id="hobbies1" value="Esporte" v-model="infos.Hobbies">
                            <label for="hobbies1">Esportes</label>

                            <input type="checkbox" id="hobbies2" value="Viagens" v-model="infos.Hobbies">
                            <label for="hobbies2">Viagens</label>

                            <input type="checkbox" id="hobbies3" value="Música" v-model="infos.Hobbies">
                            <label for="hobbies3">Músicas</label>

                            <input type="checkbox" id="hobbies4" value="Leitura" v-model="infos.Hobbies">
                            <label for="hobbies4">Leitura</label>

                            <input type="checkbox" id="hobbies5" value="VIdeoGame" v-model="infos.Hobbies">
                            <label for="hobbies5">Video Game</label>
                        </div>
                        <div>
                            <p class="titulo">Linguagem preferida:</p>
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
                        <div class="inputBio">
                            <label for="bio">Biografia</label>
                            <textarea type="text" id="bio" placeholder="Sua Biografia (opcional)"
                                v-model="infos.Biografia"></textarea>
                        </div>

                        <div class="botaoEnviar">
                            <button v-if="infos.Senha == infos.ConfSenha && infos.Senha.length >= 8"
                                type="submit">Enviar</button>
                        </div>
                    </form>
                </div>

                <div id="infosEnviadas" v-show="showprofile">
                    <h1>SEUS DADOS</h1>
                    <p>Nome: {{ infos.Nome }}</p>
                    <p>Nascimento: {{ infos.Nascimento }}</p>
                    <p>Email: {{ infos.Email }}</p>
                    <p>Cidade: {{ infos.Cidade }}</p>
                    <p>Estado: {{ infos.Estado }}</p>
                    <p>Hobbies: {{ infos.Hobbies.join(', ') }}</p>
                    <p>Linguagem Preferida: {{ infos.LinguagemProg }}</p>
                    <div class="Bio">
                        <p> Biografia: {{ infos.Biografia }}</p>
                    </div>
                    <button @click="EsconderPerfil()">Voltar</button>
                </div>

            </main>
        </div>


    </body>
</template>

<style scoped>
body {
    font-family: 'Arial', sans-serif;
    background-color: #909090;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

main {
    background-color: #d0d0d0;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 500px;
}

.containerForm {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
}

.containerForm h1 {
    text-align: center;
}

.containerForm label {
    font-weight: bold;
}

.containerForm input {
    padding: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

.containerForm select {
    padding: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

.botaoEnviar {
    display: flex;
    justify-content: center;
}

.containerForm button {
    padding: 10px 20px;
    border-radius: 5px;
    border: none;
    background-color: #003cff;
    color: #fff;
    cursor: pointer;
    font-size: 13px;
    font-weight: bold;
    transition: background-color 0.3s ease;
}

.containerForm button:hover {
    background-color: #121d5c;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    -webkit-appearance: none;
}

input[type=number] {
    -moz-appearance: textfield;
}

#infosEnviadas {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

#infosEnviadas h1 {
    text-align: center;
}

#infosEnviadas button {
    padding: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
    background-color: #ff0000;
    color: #fff;
    cursor: pointer;
}

#infosEnviadas button:hover {
    background-color: #990707;
}

.Bio {
    display: flex;
    flex-direction: column;
    height: 40px;
    gap: 5px;
}

.InputLabel {
    display: flex;
    margin: 5px;
    flex-direction: column;
    gap: 5px;
}

.inputBio {
    display: flex;
    margin: 5px;
    flex-direction: column;
    gap: 5px;
}

textarea {
    resize: none;
    padding: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
}
.titulo {
    font-weight: bold;
    margin: 10px 0 5px 0;
}
</style>
