<template> 
    <div class="justify-content-center">
        <h1>Cadastro de usuários</h1>
        <div class="row">
            <div class="col-md-12">
                <div class="table-responsive">
                    <table class="table table=striped">
                        <thead class="table-dark">
                            <tr>
                                <th>Nome</th>
                                <th>Login</th>
                                <th class="text-end">Ações</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="usuario in usuarios" :key="usuario.id">
                                <td>{{ usuario.nome }}</td>
                                <td>{{ usuario.login }}</td>
                                <td class="text-end">
                                    <router-link :to="{name:'edit', params: {id: usuario.id}}" class="btn btn-success me-2">Editar</router-link>
                                    <button @click.prevent="excluir(usuario)" class="btn btn-danger">Excluir</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>   
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default{
    data(){
        return {
            usuarios: []
        }
    },
    created(){
        let apiURL = 'http://localhost:3000/usuarios';
        axios.get(apiURL).then((resultado) => {
            this.usuarios = resultado.data
        }).catch(error => {
            console.log(error);
        })
    },
    methods:{
        excluir(contato){
            alert(JSON.stringfy(contato));
        }
    }
}
</script>