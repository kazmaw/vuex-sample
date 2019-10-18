<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>モックかどうか{{ env }}</h2>
    <ul>
      <li v-for="todo in todos" :key="todo.id">{{ todo.title }}</li>
    </ul>
  </div>
</template>

<script>
import Api from '../apis/api.js';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      env: null,
      todos: null,
    }
  },
  mounted() {
    this.env = process.env.VUE_APP_USE_MOCK
    this.getTodos();
  },
  methods: {
    getTodos () {
      Api.getTodos()
        .then(response => {
          this.todos = response.data;
        })
        .catch(error => {
          console.error(error);
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
