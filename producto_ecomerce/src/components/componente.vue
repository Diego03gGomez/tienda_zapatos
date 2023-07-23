<template lang="">
    <div>
      <header>
   


<div class="cont_header">
    <i v-on:click="menu_desplegable()" class="fa-solid fa-bars icono"></i>

<div class="cont_oculto">
<a href="">Collections</a>
<a href="">Men</a>
<a href="">Woman</a>
<a href="">About</a>
<a href="">Contact</a>
</div>


<div class="nav1">
<h1>sneakers</h1>

<nav>
    <ul>
        <a href="">Collections</a>
        <a href="">Men</a>
        <a href="">Women</a>
        <a href="">About</a>
        <a href="">Contact</a>
    </ul>
</nav>

</div>

<div class="carrito_cont ocultar">
<div v-for="(e, index) in guardados" :key="index" class="card_g">
    <div  class="img_card_g">
        <img :src=e.img alt="">
    </div>
    <div class="info_g">
<h3>Fall Limited Edition Sneakers</h3>
<h3>${{precio}}.00  x  {{e.cantidad}}   <span>${{precio * e.cantidad == 0? 125 : precio * e.cantidad  }}</span>   </h3>
    </div>
    <i v-on:click="eliminar(index)"   class="fa-solid fa-trash tacho"></i>

</div>



</div>

<div class="nav2">
    <i v-on:click="toglemenu()"   class="fa-solid fa-cart-shopping carrito"></i>
    
    <div class="cont_img_avatar">
       <img src="https://th.bing.com/th/id/OIP.Gekjb7yIYC1nmLUsMwjzzwAAAA?pid=ImgDet&w=100&h=100&c=7&dpr=1,3" alt="">
    </div>
</div>




</div>

      </header>



<div id="fondo_principal">
    <div class="cont_todo">



<div class="cont_productos">

    
<div class="producto_principal">

    <img :src="imagen_principal" alt="">

</div>

<div class="otros_productos">
<div v-on:click="seleccionar_imagen($event)"  class="card">
<img class="el_seleccionado" src="https://www.smooth.fr/wp-content/uploads/sites/39/2023/01/chaussure-1-1097x1536.jpg" alt="">
</div>

<div v-on:click="seleccionar_imagen($event)"   class="card">
<img src="https://sneakersfan.nl/wp-content/uploads/2020/11/mojtaba-fahiminia-T9IqDhJVhEU-unsplash-1463x2048.jpg" alt="">
</div>

<div v-on:click="seleccionar_imagen($event)"    class="card">
<img src="https://www.s-treatment.com/_p/acre/8718/images/pc/d1ac8cf0.jpg" alt="">
</div>

<div v-on:click="seleccionar_imagen($event)"   class="card">
<img src="https://stock-solution.de/app/uploads/2022/02/mojtaba-fahiminia-CQzCMx_wvk4-unsplash-1.jpg" alt="">
</div>


</div>



</div>


<div class="cont_descripcion">
<h3>SNEAKERS COMPANY</h3>
<h1>Fall Limited Edition <br> Sneakers</h1>
<h4>These low-profile sneakers are your perfecrt casual wear <br> companion. Featuring a durable rubber outer sole, they ll <br> withstand everythins the weather can offer</h4>
<div class="precio">
    <h2>${{precio}}.00</h2><a class="oferta" >50%</a>
</div>

<h4 class="tachado" >$250.00</h4>










<div class="cont_botones">
<div class="contador">
<button  v-on:click="restar"  >-</button>
<a class="numero"   >{{contador}}</a>
<button v-on:click="aumentar" >+</button>
</div>


<a v-on:click="agregar()" class="añadir"   ><i class="fa-solid fa-cart-shopping"></i> Add to cart</a>

</div>

</div>




</div>


</div>







    </div>
</template>
<script>
export default {

data() {
    return {
precio: 125,
contador: 0,
guardados: [
   
],
imagen_principal : "https://www.smooth.fr/wp-content/uploads/sites/39/2023/01/chaussure-1-1097x1536.jpg"
  
    }
},

methods: {
    restar() {
if(this.contador > 0){
    this.contador= this.contador-1
}

    },


    aumentar(){
        this.contador = this.contador+1
    },

agregar(){

let producto = document.querySelector(".producto_principal").querySelector("img").src;
let cantidadelegida = document.querySelector(".numero").textContent

this.guardados.push({img : producto, cantidad : cantidadelegida})

},
seleccionar_imagen(event){
 let img_prin = event.currentTarget.querySelector("img").src;  

this.imagen_principal = img_prin;

let todasImagenes = document.querySelectorAll(".card img");
      todasImagenes.forEach((imagen) => {
        imagen.classList.remove("el_seleccionado");
      });


let imagen =  event.currentTarget.querySelector("img");
imagen.classList.add("el_seleccionado")



},

toglemenu(){

let carrito = document.querySelector(".carrito_cont");
carrito.classList.toggle("ocultar")

},
eliminar(index){
    this.guardados.splice(index,1);
},
menu_desplegable(){
    let menu = document.querySelector(".cont_oculto");
    menu.classList.toggle("trasladar")
}


},









    
}
</script>
<style lang="">
    





</style>