<template>
  <form 
    @submit.prevent="createNewTodo"
    class="todolist__form">
    <input 
      v-model="newItem['name']"
      class="todolist__form-text" 
      type="text" />
    <input 
      class="todolist__form-submit" 
      type="submit" 
      value="new todo" />
  </form>
</template>

<script>
export default {
  props: ['createNewTodo', 'newItem']
}
</script>