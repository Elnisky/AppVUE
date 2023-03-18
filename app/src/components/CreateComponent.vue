<template>
    <div class="row justify-content-center">
        <div class="col-md-6">
            <h1>Novo usuário</h1>
            <form @submit.prevent="handleSubmitForm">
                <div class="form-group">
                    <label for="nome">Nome</label>
                    <input type="text" class="form-control" v-model="usuario.nome" required>
                </div>
                <div class="form-group">
                    <label for="login">Login</label>
                    <input type="text" class="form-control" v-model="usuario.login" required>
                </div>                
                <div class="form-group">
                    <label for="senha">Senha</label>
                    <input type="Password" class="form-control" v-model="usuario.senha" required>
                </div>   
                <div class="form-group">
                    <label for="confirmasenha">Confirmar senha</label>
                    <input type="Password" class="form-control" v-model="usuario.confirmasenha" required>
                </div>                                
                <div class="form-group mt-3">
                    <button class="btn btn-success btn-block w-100" type="submit">Confirmar</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default{
    data(){
        return {
            usuario: {
                id: '',
                nome: '',
                login: '',
                senha: '',
                confirmasenha: ''
            }
        };
    },
    methods: {
        handleSubmitForm(){
            let apiURL = 'http://localhost:3000/usuarios';
            if (this.usuario.senha == this.usuario.confirmasenha) {
                axios.post(apiURL, this.usuario).then(() =>{
                    alert('salvo com sucesso');
                }).catch(error => {
                    console.log(error);
                })
            }
            else
                alert('senha e confirmação não conferem');
        }
    }
}
</script>