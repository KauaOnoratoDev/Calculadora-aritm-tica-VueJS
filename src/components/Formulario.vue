<script setup>
const props = defineProps(['num1', 'sinal', 'num2', 'filtro', 'adicao', 'subtracao', 'multiplicacao', 'divisao', 'trocaSinal'])
</script>

<template>
    <div class="container">
        <form>
            <div class="row justify-content-center align-items-center">
                <div class="col-2">
                    <input @change="props.num1" class="w-100 text-center" type="number" />
                </div>
                <div class="col-1 text-center">
                    <span>{{ props.sinal }}</span>
                </div>
                <div class="col-2">
                    <input @change="props.num2" class="w-100 text-center" type="number" />
                </div>
                <div class="col-1 text-center">
                    <span>=</span>
                </div>
                <div class="col-3">
                    <span v-if="props.filtro === 'adicao'" class="form-control text-center">{{ props.adicao }}</span>
                    <span v-if="props.filtro === 'subtracao'" class="form-control text-center">{{ props.subtracao }}</span>
                    <span v-if="props.filtro === 'multiplicacao'"
                        class="form-control text-center">{{ props.multiplicacao }}</span>
                    <span v-if="props.filtro === 'divisao'" class="form-control text-center">{{ props.divisao }}</span>
                </div>
                <div class="col">
                    <select @change="props.trocaSinal"
                        class="form-control bg-secondary text-light text-center">
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