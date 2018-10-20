<template>
  <div id="app">
    <div class="content">
        <img src="./assets/logo.png">
        <h1>{{ msg }}</h1>
        <TodoList></TodoList>
    </div>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
    name: "app",
    data() {
        return {
            msg: "Concise Todo"
        };
    },
    components: {
      TodoList
    }
};
</script>

<style>
#app {
    width: 40%;
    margin: 0 auto;
    padding: 10px 0;
    border-radius: 10px;
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    box-shadow: 1px 1px 5px #ccc;
    margin-top: 60px;
}

.content {
    margin: 0 auto;
    width: 90%;
}

img {
    width: 100px;
}

h1,
h2 {
    font-weight: normal;
}

a {
    color: #42b983;
}
</style>
