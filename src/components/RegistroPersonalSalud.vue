<template>
    <br>
    <div>
        <center><h1>Registro personal salud</h1></center>
        <br>
    </div>
    <div class="RegistroPersonalSalud">
        <div class="container_RegistroPersonalSalud">
            <form v-on:submit.prevent="processRegitroPersonalSalud">
                <br>
                <label  id="ps_username">Usuario:
                <input  type="text" v-model="personalSalud.ps_username" placeholder="Username" required>
                </label>
                <br>
                <br>
                <label>Rol:
                <select  id="ps_rol" v-model="personalSalud.ps_rol">
                    <option>Médico(a)</option>
                    <option>Enfermero(a)</option>
                </select>
                </label>
                <br>
                <br>
                <label id="ps_especialidad">Perfil:
                <input type="text" v-model="personalSalud.ps_especialidad" placeholder="Especialidad" required>
                </label>
                <br>
                <br>
                <button>Registrar</button> 
            </form>
            <br>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default{ 
    data:function(){
        return{
            personalSalud:{
                ps_username:"",
                ps_rol:"",
                ps_especialidad:"",
            }
        }
    },

    methods:{
        processRegitroPersonalSalud:function(){
            
            axios.post("https://hos-casa-fe.herokuapp.com/psalud/", this.personalSalud,{headers:{}})
            
            .then((result)=>{
                alert("Registro Exitoso");

            }).catch((error)=>{
                console.log(error)
                alert("Error: falló el registro");

            })
        }
    }
}
</script>

<style>
.RegistroPersonalSalud{
    margin: 0;
    padding: 0%;
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.container_RegistroPersonalSalud{
    border: 3px solid #283747;
    border-radius: 10px;
    width: 25%;
    height: 85%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.RegistroPersonalSalud h2{
    color: #283747;
}

.RegistroPersonalSalud form{
    width: 70%;
}

.RegistroPersonalSalud input{
height: 40px;
width: 100%;
box-sizing: border-box;
padding: 10px 20px;
margin: 5px0;
border: 1px solid #283747;
}

.RegistroPersonalSalud button{
    width: 100%;
    height: 40px;
    color: #E5E7E9;
    background: #36a9cb;
    border: 1px solid #E5E7E9;
    border-radius: 5px;
    padding: 10px 25px;
    margin: 5px0 25px0;
}

.RegistroPersonalSalud button:hover{
    color: #E5E7E9;
    background: #ffab42;
    border: 1px solid #283747;
}
.RegistroPersonalSalud input{
        margin-top:10px;
        margin-bottom:5px;
    }   
    .RegistroPersonalSalud form{
        margin-top:10px;
        margin-bottom:5px;
    }  
</style>
