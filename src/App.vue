<script setup>
import { reactive } from 'vue';
import Cabecalho from "./components/Cabecalho.vue"
import Formulario from "./components/Formulario.vue"

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
  <div class="container mt-4 p-3 w-50 container-bg rounded">
    <Cabecalho />
    <Formulario :limpa-formulario="limpaFormulario" :altera-filtro="evento => estado.filtro = evento.target.value" 
      :captura-numero-um="capturaNumeroUm" :captura-numero-dois="capturaNumeroDois" :resultado="estado.resultado"/>
  </div>
</template>
<style scoped>
  .container-bg {
    background-color: blanchedalmond;
  }
</style>
