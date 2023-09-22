
<script setup>
import { ref } from 'vue'
const word = ref('')
const arr_word = ref([])
const addToArr = () => {
    if (word.value == '') {
        alert('空白は登録できません！')
    } else {
        arr_word.value.push(word.value)
        word.value = ''
    }
}
const remToArr = (index) => {
    arr_word.value.splice(index, 1)
}
</script>

<template>
    <input type="text" size=30 v-model="word">
    <button @click="addToArr()">追加</button>
    <ul v-if="arr_word.length > 0">
        <li v-for="(val_word, i) in arr_word" :key=i>{{ i + 1 }}.{{ val_word }}　
            <span @click="remToArr(i)" style="cursor:pointer">×</span>
        </li>
        <p> --- total:{{ arr_word.length }} --- </p>
    </ul>
    <p v-else> ※追加してください </p>
</template>
