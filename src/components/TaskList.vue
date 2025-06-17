<script setup lang="ts">
import { ref } from 'vue'

interface Task {
  name: string
  isCompleted: boolean
}

const Tasks = ref<Task[]>([
  { name: 'なろう講習会完走', isCompleted: false },
  { name: 'Kaggleで失ったものを取り返す', isCompleted: false }
])
const newTaskName = ref('')

const addTask = () => {
    if (newTaskName.value.trim() === '') {
        alert('タスク名を正しく入力してください。')
        return
    }
    Tasks.value.push({ name: newTaskName.value, isCompleted: false })
    newTaskName.value = ''
    alert('タスクを追加しました。')
}

</script>

<template>
  <div>
    <div>TaskList</div>
    <div>未完了:</div>
    <ul v-for="Task in Tasks" :key="Task.name" >
      <li v-if="Task.isCompleted==false">
        <div>
            {{ Task.name }}
            <input type="checkbox" v-model="Task.isCompleted" :true-value="true" :false-value="false">
        </div>
      </li>
    </ul>
    <div>完了済み:</div>
    <ul v-for="Task in Tasks" :key="Task.name">
      <li v-if="Task.isCompleted==true">
        <div>
            {{ Task.name }}
            <input type="checkbox" v-model="Task.isCompleted" :true-value="true" :false-value="false">
        </div>
      </li>
    </ul>
    <div>
      <label>
        タスク名
        <input v-model="newTaskName" type="text" />
      </label>
      <button @click="addTask">add</button>
    </div>
  </div>
</template>

<style>
</style>