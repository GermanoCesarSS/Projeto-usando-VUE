<template>
  <div class="position-absolute top-50 start-50 translate-middle border p-5 rounded">
    <h1 class="text-center">Operação de subritração</h1>
    <form @submit.prevent="subtracao()">
      <div class="col">
        <label for="n1">1° Número</label>
        <input type="number" :disabled="campoDesabilitado" name="n1" id="n1"
        class="form-control" v-model="n1"/>
      </div>
      <div class="col mt-3">
        <label for="n2">1° Número</label>
        <input type="number" :disabled="campoDesabilitado" name="n2" id="n2" 
        class="form-control" v-model="n2"/>
      </div>
      <div class="col text-center mt-3 d-grid gap-2">
        <button type="submit"
        class="btn btn-success">Subtrair</button>
        <button type="button" @click="limparReferencias()"
        class="btn btn-secondary">Limpar</button>
        <router-link to="/"
        class="btn btn-warning">Voltar</router-link>
      </div>
    </form>
    <h3 v-if="sub != null" class="mt-3 text-center" >
      O produto entre {{ n1 }} e {{ n2 }} é {{ sub }}
    </h3>
  </div>
</template>
<script setup>
  import {ref} from 'vue'

  const n1 = ref(0)
  const n2 = ref(0)

  const sub = ref(null) 
  const campoDesabilitado = ref(false)

  function subtracao(){
    sub.value = n1.value - n2.value
    campoDesabilitado.value = true
  }

  function limparReferencias(){
    n1.value = n2.value = 0
    sub.value = null
    campoDesabilitado.value = false
  }
  
</script>