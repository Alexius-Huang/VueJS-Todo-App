<template>
  <section>
    <h1>TODO Blank Slate</h1>

    <ul>
      <li v-for="item in todos" :key="item.key" v-bind:data-sth="item.key">
        <div class="item" v-show="!item.completed">
          {{ item.title }}
        </div>
      </li>
    </ul>

    <div class="input-wrapper">
      <input type="text" v-bind:value="input" @input="handleTextFieldChange" />
      <button @click="handleAddTodo">Add Todo</button>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Todo',

  data() {
    return {
      todos: [
        { key: 1, title: 'Learn Vue', completed: false, },
        { key: 2, title: 'Prepare Exit Pitch', completed: true },
        { key: 3, title: 'Prepare FLUX architecture', completed: false },
      ],

      input: 'Your Text Here',
    };
  },
  methods: {
    handleTextFieldChange(event) {
      this.input = event.target.value;
    },
    handleAddTodo() {
      const input = this.input;
      this.todos[3] = { key: 4, title: input };
      this.input = '';
    },
    filterUndoneItem(list) {
      return list.filter(item => !item.completed);
    },
  },
  computed: {
    undoneItems() {
      return this.todos.filter(item => !item.completed);
    },
  },
  watch: {},
  updated() {},
  mounted() {},
  beforeDestroy() {},
  destroyed() {},
};
</script>

<style scoped>
</style>
