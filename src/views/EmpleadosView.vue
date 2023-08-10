<template>
    <div class="empleado">
        <div class="components">
        <FormularioEmpleados/>
        <TablaEmpleados/>
        </div>
    </div>
</template>

<script>
import FormularioEmpleados from "@/components/FormularioEmpleados.vue";
import TablaEmpleados from "@/components/TablaEmpleados.vue";

export default {
name: 'EmpleadosView',
    components:{
        FormularioEmpleados,
        TablaEmpleados,
    }
}
</script>

<style>
body{
    font-family: 'Roboto', sans-serif;
    background-color: #b0cfe9;
    padding: 1%;
    display: flow-root;
    min-height: 100vh;
}

.components{
    display:grid;
    grid-template-columns: 1fr 2fr;
    grid-auto-rows: 1fr;
}

.container{

    margin:1rem;
    padding: 1rem;
    background-color: #d1dde8;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    border-radius: 15px;
    
}

h1 {
    text-align: center;
    margin-bottom: 20px;

}

.form-group{
    margin-bottom: 15px;
}

form{
   
    background-color:rgb(216, 235, 255) ;
    margin: auto;
    width: 80%;
    max-width: 350px;
    padding: 3.5em 3em;
    border-radius: 20px;
    box-shadow: 0 15px 25px -5px rgb(33, 11, 146);
    text-align:start;
    

}

label{
    display: flex;
    margin-bottom: 5px;
    font-weight: bolder;
    
}

input{
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 3px;
}

button{
    display: block;
    width: 100%;
    padding: 15px;
    background: #3866f2;
    color: #fff;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 700;
    text-transform: initial;
          
}

button:hover{
    background-color: #0056b3;
}

table{
    box-shadow: 0 15px 25px -5px rgb(33, 11, 146);
    border-collapse: collapse;
    width: 100%;
    background: #b0cfe9;
    color: #020202;
    font-size: 1rem;
    padding: .6em .3em;
    border:none;
    outline: none;
    font-family: 'roboto', sans-serif;
    cursor: pointer;
}

th,td{
    padding: 15px;
    text-align: center;
    border-style: solid;
    
}

tr{
    border-style: solid;
    
}

th{
    background-color: #007bff;
    color: #000000;
    border-style: solid;
    text-transform: initial;
    cursor: text;
}

tr:hover{
    background-color: #f5f5f5;
    
}



</style>