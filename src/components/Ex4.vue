<script setup>
import { ref } from 'vue'
const items = ref(['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'])

// TODO: Add Code Here
function addItem() {
    newItem.value = newItem.value.trim()
    if (newItem.value == "") {
        return
    }
    items.value.push(newItem.value)
    newItem.value = ""
}

const newItem = ref('')
function delItem(index) {
    items.value.splice(index, 1)
    // if you make reference to a variable, use .value to call 
    // if you put it directly in the v-functions, no need .value 
    // you can just chuck it in the template below but it confusing
}

</script>

<template>

    <h2>Shopping Cart</h2>
    <!-- TODO: Add Code Here -->
    <ul>
        <li v-for="(item, index) in items" :key="index">
            {{ item }}
            <button @click="delItem(index)">Delete!</button>
            <!-- <button @click="items.splice(index, 1)"></button> -->
        </li>
    </ul>
    <input type="text" v-model="newItem" @keyup.enter="addItem">
    <button @click="addItem()">Add!</button>
    <!-- <button @click="items.push(newItem)">Add!</button> -->

   
</template>
