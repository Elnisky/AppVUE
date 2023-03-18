<template>
    <div class="row justify-content-center">
        <div class="col-md-6">
            <h1>Editar usuário</h1>
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
            usuario: {}
        };
    },
    created(){      
        let apiURL = 'http://localhost:3000/usuarios/';
        axios.get(apiURL + this.$route.params.id).then((res) => {
             this.usuario = res.data
        }).catch(error => {
            console.log(error)
        })
    },
    methods: {
        handleSubmitForm(){
            let apiURL = 'http://localhost:3000/usuarios/';
            if (this.usuario.senha == this.usuario.confirmasenha) {
                axios.put(apiURL + this.$route.params.id, this.usuario).then(() =>{
                    alert('salvo com sucesso');
                }).catch(error => {
                    alert(error);
                })
            }
            else
                alert('senha e confirmação não conferem');
        }
    }    
}
</script>