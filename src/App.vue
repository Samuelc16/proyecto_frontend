<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
     <router-link to="/empleados">Empleados</router-link> 
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: 'roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}

nav {
  padding: 20px;
  }

nav a {
  font-weight: bolder;
  color: #100101;
  cursor: pointer;
  text-decoration: none;
  list-style-type: none;
    
  
}

nav a.router-link-exact-active {
  color: #3866f2; 
  cursor: pointer;
  display:contents;
  background: #3866f2;
  
}


</style>
