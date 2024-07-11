<script setup>
    const props = defineProps(["limpaFormulario", "alteraFiltro", "capturaNumeroUm", "capturaNumeroDois", "resultado" ])
</script>

<template>
    <form @submit="props.limpaFormulario">
        <div class="row d-flex justify-content-between">
            <div class="col-md-5">
                <select id="" class="form-control border border-success"
                    @change="props.alteraFiltro">
                    <option value="todas">Escolha a Operação Desejada</option>
                    <option value="adicao">Adição</option>
                    <option value="subtracao">Subtração</option>
                    <option value="multiplicacao">Multiplicação</option>
                    <option value="divisao">Divisão</option>
                </select>
            </div>
            <div class="col-md-3">
                <input required @keyup="props.capturaNumeroUm" type="number" placeholder="1º número"
                    class="form-control border border-success">
            </div>
            <div class="col-md-3">
                <input required @keyup="props.capturaNumeroDois" type="number" placeholder="2º número"
                    class="form-control border border-success">
            </div>
        </div>
        <div class="row mt-4">
            <div class="col-md-2">
                <label class="fw-bold" for="resultado">Resultado:</label>
            </div>
            <div class="col-md-3">
                <input :value="props.resultado" type="number" class="form-control border border-success">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Limpar</button>
            </div>
        </div>
    </form>

</template>