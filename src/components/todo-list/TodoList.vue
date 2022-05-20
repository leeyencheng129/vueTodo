<template>
  <ol class="list-group list-group-numbered mt-4">
    <li class="list-group-item d-flex justify-content-between align-items-start" v-for="item in list" :key="item.id">
      <div class="ms-2 me-auto">

        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="" :id="item.id" v-model="item.done"/>
          <label class="form-check-label" :class="item.done ? 'delete' : ''" :for="item.id" >
            {{item.task}}
          </label>
        </div>
      </div>
      <span class="badge bg-success rounded-pill" v-if="item.done">完成</span>
      <span class="badge bg-warning rounded-pill" v-else>未完成</span>
    </li>

  </ol>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    list: {
      type: Array,
      required: true,
      default: []
    }
  }
}
</script>

<style lang="less" scoped>
.list-group{
  width: 400px;
  margin: auto;
}
.delete{
  color:gray;
  text-decoration: line-through;
}
</style>