<template>
    <div class="container">
         <h1>Tabla de empleados</h1>
        <table>
            <thead>
                <tr>
                    <th>Codigo</th>
                    <th>Nombre</th>
                    <th>Apellido</th>
                    <th>Edad</th>
                    <th>Contraseña</th>
                </tr>
            </thead>
            <tbody>

                <tr v-for="empleado in empleados" :key="empleado.codigo">
                <td>{{ empleado.codigo }}</td>
                <td>{{ empleado.nombre}}</td>
                <td>{{ empleado.apellido}}</td>
                <td>{{ empleado.edad }}</td>
                <td>{{ empleado.contraseña }}</td>
                </tr>

                <router-view />
            </tbody>
        </table>
    </div>
    </template>



    <script>
        import  axios  from "axios";

        export default{
            data(){
            return {
                empleados: [],
            };
        },

        methods: {
            obtenerEmpleados() {
                axios.get('http://localhost:8080/api/empleados/listar')
                .then((response) => {
                    this.empleados = response.data;
                })
                .catch((error) => {
                    console.error("Error al obtener empleados:", error);
                });
            },
            },
            mounted(){
                //Llamar al metodo para obtener la lista de empleados al cargar el componente
                this.obtenerEmpleados();
            },
        };
    </script>
