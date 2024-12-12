
<script setup>

import { ref,computed } from 'vue';

const contador = ref(0);
const arrayFavoritos = ref([]);


const clases = computed(() =>{

  if (contador.value < 0){
    return "red"
  }
  if(contador.value > 0){
    return "green"
  }
  if(contador.value === 0){
    return"peru"
  }


})

const incrementar = () => {

  contador.value ++;

}

const decrementar = () => {

contador.value --;

}

const resetear = () => {

contador.value = 0;

}

const añadir = () => {

  arrayFavoritos.value.push(contador.value);

}

const blockButton = computed(() =>{

  const numeroRepetido = arrayFavoritos.value.find((num) => num === contador.value)

  if (numeroRepetido === 0 || numeroRepetido) {return true} else {return false}



})




  
  

</script>



<template>

<div class="container text-center mt-3">
  <h1>CONTADOR</h1>
  <h1 :class ="clases">{{ contador }}</h1>

  <button @click = "incrementar" class="btn btn-success">INCREMENTAR</button> 
  <button @click = "decrementar" class="btn btn-danger">DECREMENTAR</button>
  <button @click = "resetear" class ="btn btn-secondary">RESETEAR</button>
  <button :disabled = "blockButton" @click = "añadir" class="btn btn-primary">AÑADIR</button>


  <ul class="list-group">
   <li class="list-group-item" v-for ="numero in arrayFavoritos">
     {{ numero }}

   </li>


  </ul>

</div>
 
  

  
</template>

<style>

  .red{color:red;}
  .green{color:green;}
  .peru{color:peru;}
  

</style>