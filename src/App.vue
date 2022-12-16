<script setup>
  import { ref, computed } from 'vue';

  const cont = ref(0);

  const isInArray = computed(() =>{
    const numSearch = arrayFavs.value.find(num => num === cont.value);
    if(numSearch === 0) return true;
    return numSearch ? true : false;
  });
  const arrayFavs = ref([]);
  const increment = () => {
    cont.value++;
  };
  const dencrement = () => {
    cont.value--;
  };
  const reset = () => {
    cont.value = 0;
  };


  const add = computed(() => {
    arrayFavs.value.push(cont.value);
  });


  const classChanger = computed(() => {
    if(cont.value === 0){
      return 'zero'
    }else
    if(cont.value > 0){
      return 'positive'
    }else
    if(cont.value < 0){
      return 'negative'
    }
  });
</script>

<template>
  <h1>Añade números a la lista</h1><br>
  <button @click="increment" class="btn btn-success">Aumentar</button>
  <button @click="dencrement" class="btn btn-danger">Disminuir</button>
  <button @click="reset" class="btn btn-secondary">Reset</button>
  <button :disabled="isInArray" @click="add" class="btn btn-primary">Add</button>
  

  <h2 :class="classChanger">{{cont}}</h2>
  <h2>{{arrayFavs}}</h2>
</template>

<style>
  h1 {
    color: white;
  }
  .positive {
    color: green;
  }
  .negative {
    color: red;
  }
  .zero {
    color: yellow;
  }
</style>