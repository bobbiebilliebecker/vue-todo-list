<template>
  <div class="todolist">
    <h1 class="todolist__title">Todo List</h1>
    <ul class="todolist__list">
      <li 
        v-for="(item, index) in list" 
        v-bind:class="item.done ? 'todolist__list-item todolist__list-item--done' : 'todolist__list-item'">
        <input 
          @click="toggleChecked(index)"
          type="checkbox"
          v-bind:checked="item.done" 
          class="todolist__list-item-checkbox" />
          <span class="todolist__list-item-text">
            {{item.name}}
          </span>
      </li>
    </ul>
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
  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        message: 'hello world',
        newItem: {
          name: null,
          done: false
        },
        list: [
          {
            name: 'Get groceries',
            done: true,
          },
          {
            name: 'Walk the dog',
            done: false
          }
        ]
      };
    },
    methods: {
      toggleChecked: function(index) {
        this.list[index]['done'] = !this.list[index]['done'];
      },
      createNewTodo: function() {
        this.list.push(this.newItem);
        this.newItem = { name: null, done: false }
      }
    }
  };
</script>

<style scoped>
  .todolist {
    font-family: 'Helvetica', sans-serif;
    width: 768px;
    margin: 50px auto;
    text-align: left;
  }

  .todolist__title {
    width: 100%;
    display: block;
    font-size: 2rem;
    text-align: center;
  }

  .todolist__list {
    max-width: 80%;
    margin: 0 auto;
    list-style: none;
  }

  .todolist__list-item {
    display: block;
    margin-bottom: 1rem;
  }

  .todolist__list-item--done {
    text-decoration: line-through;
  }

  .todolist__list-item-checkbox {
    margin-right: 1rem;
  }

  .todolist__form {
    max-width: 80%;
    margin: 0 auto;
    list-style: none;
    text-align: center;
  }
</style>