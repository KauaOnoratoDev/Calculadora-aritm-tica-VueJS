<script setup>
import { reactive } from 'vue';
import Formulario from './components/Formulario.vue';
import Cabecalho from './components/Cabecalho.vue';

const estado = reactive({
    num1: Number = 0,
    num2: Number = 0,
    filtro: 'adicao',
    sinal: '+',
})

function number(x) {
    return parseInt(x)
}

function multiplicacao() {
    return estado.num1 * estado.num2
}

function subtracao() {
    return estado.num1 - estado.num2
}

function divisao() {
    return estado.num1 / estado.num2
}

function adicao() {
    return number(estado.num1) + number(estado.num2)
}

function trocaSinal() {
    if (estado.filtro === 'adicao') {
        estado.sinal = '+'
    }
    if (estado.filtro === 'subtracao') {
        estado.sinal = '-'
    }
    if (estado.filtro === 'multiplicacao') {
        estado.sinal = 'x'
    }
    if (estado.filtro === 'divisao') {
        estado.sinal = '/'
    }
}
</script>

<template>
    <Cabecalho/>
    <Formulario :num1="evento => estado.num1 = evento.target.value" :sinal="estado.sinal" :num2="evento => estado.num2 = evento.target.value" :filtro="estado.filtro" 
    :adicao="adicao()" :subtracao="subtracao()" :multiplicacao="multiplicacao()" :divisao="divisao()" :troca-sinal="evento => { estado.filtro = evento.target.value, trocaSinal()}"/>
</template>

<style scoped>
select:hover {
    cursor: pointer
}
</style>
