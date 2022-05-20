<template>
  <form class="row row-cols-lg-auto g-3 align-items-center" @submit.prevent="onFormSubmit">
    <div class="col-12">
      <label class="visually-hidden" for="inlineFormInputGroupUsername">Username</label>
      <div class="input-group">
        <div class="input-group-text">任務</div>
        <input type="text" class="form-control" id="inlineFormInputGroupUsername" placeholder="任務內容" v-model.trim="taskName">
      </div>
    </div>

    <div class="col-12">
      <button type="submit" class="btn btn-primary">添加新任務</button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'TodoInput',
 
  data() {
    return {
      taskName: ''
    }
  },
  methods: {
    onFormSubmit() {
      if (!this.taskName) return alert('不能為空')
      this.$emit('add', this.taskName)
      this.taskName = ''
    }
  }
}
</script>

<style lang="less" scoped>
</style>