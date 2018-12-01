<template>
  <container>
    <main-heading></main-heading>
    <section>
      <todo-form
        :new-item="newItem"
        :create-new-todo="createNewTodo">
      </todo-form>
    </section>
    <section>
      <section-heading
        text="incomplete"></section-heading>
      <todo-list
        :done="true"
        :list="list"
        :toggle-checked="toggleChecked">
      </todo-list>
    </section>
    <section>
      <section-heading
        text="complete"></section-heading>
      <todo-list
        :done="false"
        :list="list"
        :toggle-checked="toggleChecked">
      </todo-list>
    </section>
  </container>
</template>

<script>
import MainHeading from './components/MainHeading.vue';
import Section from './containers/Section.vue';
import SectionHeading from './components/SectionHeading.vue';
import Container from './containers/Container.vue';
import TodoList from './components/TodoList.vue'
import TodoForm from './components/TodoForm.vue'

export default {
  name: "App",
  components: {
    MainHeading,
    Container,
    Section,
    SectionHeading,
    TodoList,
    TodoForm
  },
  data() {
    return {
      message: "hello world",
      newItem: {
        name: null,
        done: false
      },
      list: []
    };
  },
  methods: {
    toggleChecked: function(index) {
      this.list[index]["done"] = !this.list[index]["done"];
    },
    createNewTodo: function() {
      this.list.push(this.newItem);
      this.newItem = { name: null, done: false };
    }
  }
};
</script>