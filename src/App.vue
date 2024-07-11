<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    numeroUm: 0,
    numeroDois: 0,
    filtro: "todas",
    resultado: 0,
  })

  const soma = () => {
    return parseFloat(estado.numeroUm) + parseFloat(estado.numeroDois)
    }

  const subtrai = () => {
    return estado.numeroUm - estado.numeroDois
    }

  const multiplica = () => {
    return estado.numeroUm * estado.numeroDois
    }

  const divide = () => {
    return estado.numeroUm / estado.numeroDois
    }

  const executaOperacao = () => {
    const {filtro} = estado;

    switch (filtro) {
      case "adicao":
        return soma();
      case "subtracao":
        return subtrai();
      case "multiplicacao":
        return multiplica();
      case "divisao":
        return divide();
      default:
        return filtro
    }
  }

  const capturaNumeroUm = (evento) => {
    estado.numeroUm = evento.target.value;
    return estado.resultado = executaOperacao();
  }

  const capturaNumeroDois = (evento) => {
    estado.numeroDois = evento.target.value;
    return estado.resultado = executaOperacao();
  }

  const limpaFormulario = () => {
    estado.filtro = "todas",
    estado.numeroUm = 0;
    estado.numeroDois = 0;
    estado.resultado = 0;
  }


</script>

<template>
  <div class="container p-3 w-50 bg-info rounded">
    <header class="p-5 mb-4 mt-2 bg-success rounded">
      <h1>Calculadora</h1>
      <p>
        Digite 2 (dois) números e escolha a operação que deseja realizar entre eles:
      </p>
    </header>  
    <form @submit.prevent="limpaFormulario">
      <div class="row d-flex justify-content-between">
        <div class="col-md-5">
          <select id="" class="form-control border border-success " @change="evento => estado.filtro = evento.target.value">
            <option value="todas">Escolha a Operação Desejada</option>
            <option value="adicao">Adição</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
        <div class="col-md-3">
          <input required @keyup="capturaNumeroUm" type="number" placeholder="1º número" class="form-control border border-success">
        </div>
        <div class="col-md-3">
          <input required @keyup="capturaNumeroDois" type="number" placeholder="2º número" class="form-control border border-success">
        </div>
      </div>      
      <div class="row mt-4">
        <div class="col-md-2" >
          <label class="fw-bold" for="resultado">Resultado:</label>
        </div>
        <div class="col-md-3">
          <input :value="estado.resultado" type="number" class="form-control border border-success">
        </div>
        <div class="col-md-2">
          <button type="submit" class="btn btn-primary">Limpar</button>
        </div>
      </div>
    </form>
  </div>
</template>
<style scoped>
</style>
