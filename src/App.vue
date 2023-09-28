<script setup>
const name = 'Marco';
// const styleColor = "color: blue";
// const arrayColores = ["blue", "red", "peru"];
// const activo = null;
// const arrayFrutas = [
//   {
//     name: "Manzana",
//     price: "$1.00",
//     description: "Una manzana",
//   },
//   {
//     name: "Pera",
//     price: "$2.00",
//     description: "Una pera",
//   },
//   {
//     name: "Naranja",
//     price: "$3.00",
//     description: "Una naranja",
//   },
//];
// const objetoFruta = {
//   name: "Manzana",
//   price: "$1.00",
//   description: "Una manzana",
//   id: 1
// };
// const arrayFrutas = [
//     {
//         name: "Manzana",
//         price: "$1.00",
//         description: "Una manzana",
//         stock: 0,
//     },
//     {
//         name: "Pera",
//         price: "$2.00",
//         description: "Una pera",
//         stock: 10,
//     },
//     {
//         name: "Naranja",
//         price: "$3.00",
//         description: "Una naranja",
//         stock: 20,
//     },
// ];
//metodo - methods
// const handleClick = (message) => {
//   console.log(message)
// }
import { ref, computed } from 'vue'
const counter = ref(0);
const numeros = ref([]);
const increment = () => {
  counter.value++;
}
const disminuir = () => {
  counter.value--
}
const reset = () => {
  counter.value = 0;
  numeros.value.length = 0;
}

const add = () => {
  numeros.value.push(counter.value);
}

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero'
  }
  if (counter.value > 0) {
    return 'positive'
  }
  if (counter.value < 0) {
    return 'negative'
  }
});

const estado = computed(() => {
  const found = numeros.value.find((val) => val === counter.value);
  //if (found === 0) return true;
  //return found ? true : false;
  return found || found === 0;
});
</script>
<template>
  <!-- <h1>Hola {{name.toUpperCase()}}</h1>
  <h2>{{ arrayColores }}</h2>
  <h2 :style="`color: ${arrayColores[2]}`">Soy Peru</h2>
  <h2>{{ activo ? 'estoy activo' : 'Estoy inactivo' }}</h2>
  <h2 v-if="activo === true">Estoy activo</h2>
  <p v-else-if="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p> 
  <h2 v-show="true">Estoy activo</h2>-->
  <!-- <ul>
    <li v-for="fruta in arrayFrutas" :key="fruta.name">
      {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}
    </li>
  </ul> -->
  <!-- <ul>
    <li v-for="(value, propiedad, index) in objetoFruta" :key="value">
      {{ index }} - {{ propiedad }} : {{ value }}
    </li>
  </ul> -->
  <!-- <ul>
      <template v-for="item in arrayFrutas" :key="item.name" >
        <li v-if="item.stock > 0">
          {{ item.name }} - {{ item.price }}
        </li>
      </template>
  </ul> -->
  <!-- <button v-on:click.right.prevent="handleClick('Texto right')">Activame right</button>
  <button @click.left="handleClick('Texto left')">Activame left</button>
  <button @click.middle="handleClick('Texto middle')">Activame middle</button> -->

  <!-- Forma 1
  <h2 v-if="counter > 0" :style="`color: green`">
    {{ counter }}
  </h2>
  <h2 v-else-if="counter < 0" :style="`color: red`">
    {{ counter }}
  </h2>
  <h2 v-else>
    {{ counter }}
  </h2> -->
  <!-- Forma 2 -->
  <!-- <h2 :class="counter>0 ? 'positive' : 'negative'">
    {{ counter }}
  </h2> -->
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <h2 :class="classCounter">
      {{ counter }}
    </h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="disminuir" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Resetear</button>
      <button @click="add" :disabled="estado" class="btn btn-primary">Agregar</button>
    </div>
    <ul class="list-group">
      <li v-for="(numero, index) in numeros" :key="index" class="list-group-item">
        {{ numero }}
      </li>
    </ul>
  </div>
</template>
<style>
.negative {
  color: red
}

.positive {
  color: green
}

.zero {
  color: peru
}
</style>