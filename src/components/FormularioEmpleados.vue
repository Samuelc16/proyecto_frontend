<template>
<div class="container">
    
    <h1>Formulario de empleados</h1>
    <form id="empleado-form" @submit.prevent="guardar">
        <div class="form-group">
            <label for="codigo">Codigo de empleado:</label>
            <input type="text" id="codigo" name="codigo" required v-model="codigo"> 
        </div>
        <div class="form-group">
            <label for="codigo">Nombre:</label>
            <input type="text" id="nombre" name="nombre" required v-model="nombre"> 
        </div>
        <div class="form-group">
            <label for="codigo">Apellido:</label>
            <input type="text" id="apellido" name="apellido" required v-model="apellido"> 
        </div>
        <div class="form-group">
            <label for="codigo">Edad:</label>
            <input type="text" id="edad" name="edad" required v-model="edad"> 
        </div>
        <div class="form-group">
            <label for="codigo">Contraseña:</label>
            <input type="text" id="ctr" name="ctr" required v-model="contraseña"> 
        </div>


        <button type="submit" id="guardar" name="guardar">Guardar</button><br>
        <button type="submit" id="buscar" name="buscar" @click="buscar"> Buscar</button><br />
        <button type="submit" id="actualizar" name="actualizar" @click="actualizar"> Actualizar</button><br />
        <button type="submit" id="eliminar" name="eliminar" @click="eliminar"> Eliminar</button><br />
        
        
        

        </form>
        
    </div>
    
    </template>

    <script>
    
    import axios from "axios";

    export default{

        data() {

            return{
                codigo: "",
                nombre: "",
                apellido: "",
                edad: "",
                contraseña: "",
            };

        },

        methods:{
            guardar(){
                axios
                .post("http://localhost:8080/api/empleados",{
                    codigo: this.codigo,
                    nombre: this.nombre,
                    apellido: this.apellido,
                    edad: this.edad,
                    contraseña: this.contraseña,
                    
                })
                .then((response) => {
                    console.log("Empleado registrado", response.data);
                    alert("cambios guardados");
                    this.codigo = '';
                    this.nombre = '';
                    this.apellido = '';
                    this.edad = '';
                    this.contraseña = '';

                })
                .catch((error) => {
                    console.error("Error al registrar empleado:", error);
                    alert("Error de registro");
                });
            },
        
            buscar(){
                axios
                .get("http://localhost:8080/api/empleados/"+this.codigo)
                .then((response) => {
                    // Actualizar los campos del formulario con los datos del empleado consultado
                    this.nombre = response.data.nombre;
                    this.apellido = response.data.apellido;
                    this.edad = response.data.edad;
                    this.contraseña = response.data.contraseña;
                    
                })
                .catch((error) => {
                    console.error("Error al buscar", error);
                    
                });
            },

            actualizar(){

                axios
                .put("http://localhost:8080/api/empleados/actualizar/{id}"+this.codigo, {
                    codigo: this.codigo,
                    nombre: this.nombre,
                    apellido: this.apellido,
                    edad: this.edad,
                    
                  })
                .then((response) => {
                    console.log("Empleado actualizado con exito:", response.data);
                })
                .catch((error) => {
                    console.error("Error al actualizar empleado:", error);
                });

            },

            eliminar() {

                axios
                    .delete("http://localhost:8080/api/empleados/"+this.codigo)
                    .then(() => {
                    alert("Empleado eliminado");
                        console.log("Empleado eliminado con exito:");
                        // Limpiar los campos del formulario despues de eliminar
                        this.codigo = "";
                        this.nombre = "";
                        this.apellido = "";
                        this.edad = "";
                        this.contraseña = "";
                })

                
                .catch((error) => {
                    console.error("Error al eliminar empleado:", error);
                    
                });
            },
        },

            
    };
        
    

</script>
