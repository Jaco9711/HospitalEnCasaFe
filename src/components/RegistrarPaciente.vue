<template>
    <h1>Registrar Paciente</h1>
    <div class="RegistroPaciente">
        <div class="container_RegistroPaciente">
            <form v-on:submit.prevent="processCreatePaciente">
                <label id="p_username">Usuario:
                <input type="text" v-model="user.p_username" placeholder="Username" required>
                </label>
                <br>
                <br>
                <label>ID Personal de Salud Asignado
                <input type="Number" v-model="user.p_personal_salud" placeholder="ID PSalud" required>
                </label>
                <br>
                <br>
                <label id="p_fecha_nacimiento">Fecha Nacimiento:
                <input type="text" v-model="user.p_fecha_nacimiento" placeholder="Año-Mes-Dia" required>
                </label>
                <br>
                <br>
                <label>Ciudad
                <select id="p_ciudad" v-model="user.p_ciudad" required>
                <option>           </option>
                <option>Bogota D.C </option>
                <option>Medellin </option>
                <option>Cali</option>
                <option>Barranquilla</option>
                </select>
                </label>
                <br>
                <br>
                <label id="p_direccion">Dirección del paciente:
                <input type="text" v-model="user.p_direccion" placeholder="Barrio-Carrera-Calle-Numero" required>
                </label>
                <br>
                <br>
                <label id="p_latitud">Latitud:
                <input type="text" v-model="user.p_latitud" placeholder="Grados°/Min/Seg">
                </label>
                <br>
                <br>
                <label id="p_longitud">Longitud:
                <input type="text" v-model="user.p_longitud" placeholder="Longitud">
                </label>
                <br>
                <br>
                <button>Registrar</button>
                <br>
                <br>
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
                    p_username:"",
                    p_personal_salud:"",
                    p_fecha_nacimiento: "",
                    p_ciudad: "",
                    p_direccion: "",
                    p_latitud: "",
                    p_longitud:""

                }
            }
        },
    
        methods:{
            processCreatePaciente:function(){
                
                axios.post("https://hos-casa-fe.herokuapp.com/regpaciente/",this.user,{headers:{}})
                
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
    .RegistroPaciente{
        margin: 0;
        padding: 0%;
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    
    .container_RegistroPaciente{
        border: 3px solid #283747;
        border-radius: 10px;
        width: 25%;
        height: 85%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    
    .RegistroPaciente h2{
        color: #283747;
    }
    
    .RegistroPaciente form{
        width: 70%;
    }
    
    .RegistroPaciente input{
    height: 40px;
    width: 100%;
    box-sizing: border-box;
    padding: 10px 20px;
    margin: 5px0;
    border: 1px solid #283747;
    }
    
    .RegistroPaciente button{
    width: 100%;
    height: 40px;
    color: #E5E7E9;
    background: #36a9cb;
    border: 1px solid #E5E7E9;
    border-radius: 5px;
    padding: 10px 25px;
    margin: 5px0 25px0;
    }
    
    .RegistroPaciente button:hover{
    color: #E5E7E9;
    background: #ffab42;
    border: 1px solid #283747;
    }

    .btn-reg{
        margin-top:10px;
        margin-bottom:5px;
    }
    .RegistroPaciente input{
        margin-top:10px;
        margin-bottom:10px;
    }   
    .RegistroPaciente form{
        margin-top:10px;
        margin-bottom:10px;
    }     
    </style>