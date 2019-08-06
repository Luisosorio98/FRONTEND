<template>
  <div id="app">
    <center>
    <h2>Usuarios</h2>
     <table border="2">
       <tr>
         <td>
           ID
         </td>
         <td>
           Nombre
         </td>
         <td>
           Apellido
         </td>
         <td>
           Telefono
         </td>
       
       <td>
         Dirección
       </td>
       <td>
         Correo
       </td>
       </tr>
     
      <tr v-for="dato in datos">
           <td>
             {{dato._id}}
           </td>
           <td>
             {{dato.nombre}}
           </td>
           <td>
             {{dato.apellido}}
           </td>
           <td>
             {{dato.telefono}}
           </td>
           <td>
            {{dato.direccion}}
           </td>
           <td>
             {{dato.correo}}
           </td>
      </tr>
     </table>
    
     <h2>Registrar Usuarios</h2>
     <form >
       <label >Nombre</label>
          <input type="text"  v-model="nombre">
           <label >Apellido</label>
          <input type="text"  v-model="apellido">
           <label >Telefono</label>
          <input type="text"  v-model="telefono">
           <label >Dirección</label>
          <input type="text"  v-model="direccion">
           <label >Correo</label>
          <input type="text"  v-model="correo">
          <input type="button" value="Registrar" @click="registrar">
     </form>
    </center>
    
  </div>
</template>

<script>

import axios from 'axios';
export default {
  name: 'app',
data:()=>({
   datos:null,
   actividades:null,
   nombre:null,
   apellido:null,
   direccion:null,
   correo:null,
   telefono:null,
   genero:null
}),
  created() {
    var vm = this
    axios.get('http://localhost:3000/users')
  .then(function(response){
    console.log(response.data);
    vm.datos =response.data
 
  });  

   
  },
methods: {
  registrar(){

		 var vm =this
					 var dato ={nombre:this.nombre, apellido:this.apellido, telefono:this.telefono, correo:this.correo, dirrecion:this.direccion}
					axios.post("http://localhost:3000/users", dato).then((res)=>{
			        
			
					console.log(res)
				 })
   
   
  
  }
},
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
