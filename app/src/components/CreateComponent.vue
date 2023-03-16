<template>
    <div class="row justify-content-center">
        <div class="col-md-6">
            <h1>Novo Contato</h1>
            <form @submit.prevent="handleSubmitForm">
                <div class="form-group">
                    <label for="nome">Nome</label>
                    <input type="text" class="form-control" v-model="contato.nome" required>
                </div>
                <div class="form-group">
                    <label for="idade">Idade</label>
                    <input type="number" class="form-control" v-model="contato.idade" required>
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
            contato: {
                id: '',
                nome: '',
                idade: ''
            }
        };
    },
    methods: {
        handleSubmitForm(){
            let apiURL = 'http://localhost:3000/contatos';
            axios.post(apiURL, this.contato).then(() =>{
                alert('salvo com sucesso');// this.@router.push
            }).catch(error => {
                console.log(error);
            })
        }
    }
}
</script>