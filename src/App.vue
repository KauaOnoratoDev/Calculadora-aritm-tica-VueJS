<script setup>
import { reactive } from 'vue';

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
        if (estado.filtro === 'divisao'){
            estado.sinal = '/'
        }
    }
</script>

<template>
    <div class="container">
        <header class="p-3 mt-5 mb-5 bg-light rounded-5 text-center">
            <h1>Calculadora Aritmética</h1>
            <p class="mt-2 mb-2">Digite dois valores para calcular seu resultado</p>
        </header>
        <form>
            <div class="row justify-content-center align-items-center">
                <div class="col-2">
                    <input @change="evento => estado.num1 = evento.target.value" class="w-100 text-center" type="number">
                </div>
                <div class="col-1 text-center">
                    <span>{{ estado.sinal }}</span>
                </div>
                <div class="col-2">
                    <input @change="evento => estado.num2 = evento.target.value" class="w-100 text-center" type="number">
                </div>
                <div class="col-1 text-center">
                    <span>=</span>
                </div>
                <div class="col-3">
                    <span v-if="estado.filtro === 'adicao'" class="form-control text-center">{{ adicao() }}</span>
                    <span v-if="estado.filtro === 'subtracao'" class="form-control text-center">{{ subtracao() }}</span>
                    <span v-if="estado.filtro === 'multiplicacao'" class="form-control text-center">{{ multiplicacao() }}</span>
                    <span v-if="estado.filtro === 'divisao'" class="form-control text-center">{{ divisao() }}</span>
                </div>
                <div class="col">
                    <select @change="evento => {estado.filtro = evento.target.value, trocaSinal()}" class="form-control bg-secondary text-light text-center">
                        <option value="adicao">Adição</option>
                        <option value="subtracao">Subtração</option>
                        <option value="multiplicacao">Multiplicação</option>
                        <option value="divisao">Divisão</option>
                    </select>
                </div>
            </div>
        </form>
    </div>
</template>

<style scoped>
select:hover {
    /* cursor: pointe */
}
</style>
