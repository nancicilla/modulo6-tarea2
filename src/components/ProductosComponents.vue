<template>
    <div class="container ">

        <div class="row">
            <h4>Productos relacionados</h4>
        </div>
        <div class="row">
            <div class="col" @click="seleccionarProducto(prelacionados.id)"  v-for="(prelacionados) in productosRelacionados" :key="prelacionados.id">
                <div class="card" style="width: 18rem;">
                    <div class="card-body">
                        <h5 class="card-title">{{prelacionados.nombre}}</h5>
                        <img :src="prelacionados.imagen"  alt="" :style="`width: 100%`">
                        <p class="card-text" v-html="prelacionados.descripcion"></p>
                            <div class="producto-relacionado-precio">Precio:{{prelacionados.precio}} BOB</div>
                        <div>
                <div>
                    <div class="color-box" :style="`background: ${colorr}`" v-for="(colorr) in prelacionados.colores" :key="colorr.id"></div>
                   
                </div>
                        </div>
                    </div>
                </div>
            </div>
            
           
        </div>
    </div>
    </template>
    
    <script>
    import axios from "axios";
    export default {
      name: 'ProductosComponents',      
      data() {
        let productosRelacionados;
        axios.get('http://localhost:5000/Productos?seleccionado=false').then(response => {
            
            this.productosRelacionados= response.data;
       }).catch(e => console.log(e));
      return{
        productosRelacionados
      }
      },
      methods:{
        seleccionarProducto(id){
           
            axios({
          method: "get",
          url: "http://localhost:5000/Productos?id_ne="+id 
        })
        .then(response =>{
            let todos=response.data
            todos.forEach(element => {
          console.log(element);
              axios({
              method: "patch",
              url: "http://localhost:5000/Productos/"+element.id ,
              data: {
                seleccionado:false
              }
            })
            .then(response =>{
              console.log(response);
            })
            .catch(e => console.log(e));
        


         });
                      
        })
        .catch(e => console.log(e));
         
        

        axios({
          method: "patch",
          url: "http://localhost:5000/Productos/"+id ,
          data: {
            seleccionado:true
          }
        })
        .then(response =>{
           console.log(response);
           window.location = window.location.href;
        })
        .catch(e => console.log(e));
       
       




        }

      }
    }
    </script>
    