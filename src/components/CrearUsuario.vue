<template>
    <h1>Crear Usuario</h1>
    <div class="RegistroUsuario">
        <div class="container_RegistroUsuario">
        <form v-on:submit.prevent="processCreateUser">
            <label>
                Usuario:
            </label>
            <input type="text" v-model="user.u_username" placeholder="Username" required>
            <br>
            <label>
                Password:
            </label>
            <input v-model="user.password" type="Password" required>  
            <br>     
            <label>
                Nombres:
            </label>
            <input v-model="user.u_nombres" type="text" placeholder="Nombres" required>                 
            <br>               
            <label>
                Apellidos:
            </label>
            <input type="text" v-model="user.u_apellidos" placeholder="Apellidos" required>            
            <br>   
            <label>
                Telefono:
            </label>
            <input type="text" v-model="user.u_telefono" placeholder="Telefono" required>            
            <br>   
            <label>
                Perfil:
            </label>
            <select v-model="user.u_perfil" id="u_perfil" required>
                <option>Personal Salud</option>
                <option>Familiar</option>
                <option>Paciente</option>
            </select>     
            <br>            
            <label>
                Genero:
            </label>
            <select v-model="user.u_genero" id="u_genero">
                <option>M</option>
                <option>F</option>
            </select>     
            <br>
            <button class="btn-reg">Registrar</button>    
        </form>
    </div>
</div>
</template>

<script>
import axios from 'axios';
export default { 
    data:function(){
        return{
            user:{
                u_username:"",
                password:"",
                u_perfil: "",
                u_nombres: "",
                u_apellidos: "",
                u_telefono: "",
                u_genero:""

            }
        }
    },

    methods:{
        processCreateUser:function(){
            
            axios.post("https://hos-casa-fe.herokuapp.com/user/", this.user,{headers:{}})
            
            .then((result)=>{
                alert("Registro Exitoso");

            }).catch((error)=>{
                console.log(error)
                alert("Error: fall?? el registro");

            })
        }
    }
}
</script>

<style>
    .RegistroUsuario{
        margin: 0;
        padding: 0%;
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    
    .container_RegistroUsuario{
        border: 3px solid #283747;
        border-radius: 10px;
        width: 25%;
        height: 85%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    
    .RegistroUsuario h2{
        color: #283747;
    }
    
    .RegistroUsuario form{
        width: 70%;
    }
    
    .RegistroUsuario input{
    height: 40px;
    width: 100%;
    box-sizing: border-box;
    padding: 10px 20px;
    margin: 5px0;
    border: 1px solid #283747;
    }
    
    .RegistroUsuario button{
    width: 100%;
    height: 40px;
    color: #E5E7E9;
    background: #36a9cb;
    border: 1px solid #E5E7E9;
    border-radius: 5px;
    padding: 10px 25px;
    margin: 5px0 25px0;
    }
    
    .RegistroUsuario button:hover{
    color: #E5E7E9;
    background: #ffab42;
    border: 1px solid #283747;
    }

    .btn-reg{
        margin-top:10px;
        margin-bottom:5px;
    }
    .RegistroUsuario input{
        margin-top:10px;
        margin-bottom:10px;
    }   
    .RegistroUsuario form{
        margin-top:10px;
        margin-bottom:10px;
    }     
    </style>