<template>
  <ul class="todolist__list">
    <li
      v-for="(item, index) in list"
      v-if="item.done === done"
      v-bind:key="index"
      v-bind:class="item.done ? 'todolist__list-item todolist__list-item--done' : 'todolist__list-item'"
    >
      <input 
        @click="toggleChecked(index)" 
        type="checkbox" 
        v-bind:checked="item.done"
        class="todolist__list-item-checkbox">
      <span class="todolist__list-item-text">{{item.name}}</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'todo-list',
  props: ['list', 'toggle-checked', 'done']
}
</script>