<template>
  <div class="app-container">
    <h1>APP</h1>
    <TodoInput @add="onAddNewTask"></TodoInput>
    <TodoList :list="tasklist"></TodoList>
  <TodoButton v-model:active="activeBtnIndex"></TodoButton>
  </div>

</template>

<script>
import TodoList from './components/todo-list/TodoList.vue'
import TodoInput from './components/todoInput/todoInput.vue'
import TodoButton from './components/todo-button/TodoButton.vue'

export default {
  name: 'App',
  data() {
    return {
      todolist: [
        { id: 1, task: '吃飯', done: false },
        { id: 2, task: '睡覺', done: false },
        { id: 3, task: '打咚咚', done: true }
      ],
      nextId:4,
      activeBtnIndex: 0
    }
  },
  computed:{
    tasklist(){
      switch(this.activeBtnIndex){
        case 0:
          return this.todolist
        case 1:
          return this.todolist.filter( x => x.done)
        case 2:
          return this.todolist.filter( x => !x.done)
      }
    }
  },
  methods: {
    onAddNewTask(taskName) {
    this.todolist.push(
      {id:this.nextId , task:taskName , done:false}
      )

      this.nextId++
    }
  },

  components: { TodoList, TodoInput , TodoButton }
}
</script>

<style lang="less">
.app-container {
  max-width: 400px;
  margin: auto;
}
</style>