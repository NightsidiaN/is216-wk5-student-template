<script setup>
import { ref, computed } from 'vue'

const x = ref(0)
const y = ref(0)
const operators = ref(["+", "-", "*", "/", "%"])
const selectedOp = ref("+")

// TODO: Add Code Here
// Note: DO NOT USE "eval()". In security, "eval" is considered "evil"!!!
const operation = {
    "+": (x, y) => x + y,
    "-": (x, y) => x - y,
    "*": (x, y) => x * y,
    "/": (x, y) => x / y,
    "%": (x, y) => x % y
}
// dictionary where the values are temporary functions 

const result = computed(() => {
    return operation[selectedOp.value](x.value, y.value)
})
// eg: operation["+"](6, 7)
// find in the dictionary: "+", then input x y values as 6 7 


</script>

<template>
    <p>x <input v-model.number="x"></p>
    <select v-model="selectedOp">
        <option v-for="op in operators">{{ op }}</option>
    </select>
    <p>y <input v-model.number="y"></p>

    <p>---------------------</p>

    <p>= {{ result }}</p>
</template>

<style scoped>
p,
input {
    font-family: monospace;
}

p {
    white-space: pre;
}
</style>
