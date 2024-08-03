<script setup lang="ts">
import { ref } from 'vue'

const iniVal = [
  {
    id: 1,
    task: '資格勉強',
    isCheck: false
  },
  {
    id: 2,
    task: '小説を読む',
    isCheck: false
  }
]

const todoAry = ref(iniVal)
const inptText = ref('')

const addTodo = () => {
  if (inptText.value.trim()) {
    const newVal = {
      id: Math.floor(Math.random() * 9999),
      task: inptText.value,
      isCheck: false
    }
    todoAry.value.push(newVal)
    inptText.value = '' // 入力欄をクリアする
  }
}
const deleteTodo = () => {
  const newTodoAry = []

  todoAry.value = []
}
</script>

<template>
  <section class="box">
    <div class="screen">
      <h1>TODO APP</h1>
      <p>残りのタスク：{{ todoAry.length }}</p>
      <input type="text" v-model="inptText" />
      <button @click="addTodo">追加する</button>
      <button @click="deleteTodo">削除する</button>
      <p v-for="(item, index) in todoAry" :key="index">{{ item.task }}</p>
      <div v-for="(item, index) in todoAry" :key="index">
        <input type="checkbox" name="item.task" v-model="item.isCheck" />
        <label for="item.task">{{ item.task }}</label>
      </div>
    </div>
  </section>
</template>

<style scoped>
.box {
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
}
.screen {
  width: 400px;
  border: 1px solid black;
  padding: 30px;
  border-radius: 10px;
}
</style>
