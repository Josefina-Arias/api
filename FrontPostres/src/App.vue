
<script>
import  axios from 'axios';

export default {

  data(){
    return{
      postres: [],
      postre:[]
    }  
  },

methods:{
  obtenerDatosPostres(){
    const respuesta = axios.get('http://192.168.209.1:3000/api/v1/products').then (response => {
      this.postres =response.data.body;
    })
     
  },  obtenerDatoPostre(id){
    const respuesta = axios.get('http://192.168.209.1:3000/api/v1/product/'+id).then (response => {
      this.postre =response.data.body;
    })
     
  }

 }, 
 mounted(){

 }
}



</script>

<template>
  <button @click="obtenerDatosPostres()">
    traerDatos
  </button>

  <table>
    <tr v-for="product in postres">
      <th >{{ product.nombre }}</th>
      <th >{{ product.precio }}</th>
      <th ><button id="product.codigo" @click="obtenerDatoPostre(product.codigo)">verInfo</button></th>

    </tr>
  </table>

  <section>
  {{ postre }}
</section>

</template>



<style >

</style>
