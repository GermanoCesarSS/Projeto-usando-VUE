<template>
  <div class="position-absolute top-50 start-50 translate-middle border p-5 rounded">
    <h1 class="text-center">Operação de multiplicação</h1>
    <form @submit.prevent="multiplicar()">
      <div class="col">
        <label for="n1">1° Número</label>
        <input type="number" name="n1" id="n1"
        class="form-control" v-model="n1"/>
      </div>
      <div class="col mt-3">
        <label for="n2">1° Número</label>
        <input type="number" name="n2" id="n2"
        class="form-control" v-model="n2"/>
      </div>
      <div class="col text-center mt-3 d-grid gap-2">
        <button type="submit"
        class="btn btn-success">Multiplicar</button>
        <button type="button" @click="limparReferencias()"
        class="btn btn-secondary">Limpar</button>
        <router-link to="/"
        class="btn btn-warning">Voltar</router-link>
      </div>
    </form>
    <h3 v-if="multiplicacao != null" >
      O produto entre {{ n1 }} e {{ n2 }} é {{ multiplicacao }}
    </h3>
  </div>
</template>
<script setup>
  import {ref} from 'vue'

  const n1 = ref(0)
  const n2 = ref(0)

  const multiplicacao = ref(null) 

  function multiplicar(){
    multiplicacao.value = n1.value * n2.value
  }

  function limparReferencias(){
    n1.value = n2.value = 0
    multiplicacao.value = null
  }
  
</script>