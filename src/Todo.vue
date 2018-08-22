<template xmlns:v-on="http://www.w3.org/1999/xhtml">
  <div>
    <img :src="logo" class="Logo">
    <h1 class="ToDo-Header">Vue To Do</h1>
    <div class="ToDo-Container">
      <div class="ToDo-Content">
        <TodoItem v-for="  todo in list"
                  :todo="todo"
                  @delete="onDeleteItem"
                  :key="todo.id"></TodoItem>
      </div>
      <input type="text" v-model="todo" v-on:keyup.enter="createNewTodo" title="enter todo">
      <div class="ToDo-Add" @click="createNewTodo">+</div>
    </div>

  </div>
</template>

<script>

  import Logo from './assets/logo.png'
  import TodoItem from './components/TodoItem'

  export default {
    name: "Todo",
    components: {
      TodoItem
    },
    data() {
      return {
        list: [{ id: 1, text: 'work' }, { id: 2, text: 'study' }],
        todo: '',
        logo: Logo

      }
    },


    methods: {
      onDeleteItem(todo) {
        this.list = this.list.filter(item => item !== todo)
      },
      createNewTodo() {
        if (!this.todo) {
          alert("please enter a todo!");
          return
        }
        const newId = Math.max.apply(null, this.list.map(t => t.id)) + 1;
        this.list.push({ id: newId, text: this.todo });
        this.todo = '';
      }
    }
  }
</script>

<style scoped>


  body {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, Helvetica Neue, Helvetica, Arial, sans-serif;
    background: linear-gradient(#aeffae, #3d99ff);
    height: auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .Logo {
    width: 50px;
    position: relative;
    top: 50px;
  }

  .Todo {
    text-align: center;
    border: 1px solid white;
    width: 80vw;
    height: auto;
    box-shadow: 2px 3px 15px rgba(0, 0, 0, 0.5);
    background: #f6f6f6;
    padding-bottom: 60px;
    margin: 40px auto;
  }

  .ToDo-Header {
    color: black;
    font-family: -apple-system, BlinkMacSystemFont, Helvetica Neue, Helvetica, Arial, sans-serif;
    font-weight: 400;
    text-transform: uppercase;
    margin: 70px auto 30px;
  }

  .ToDo-Add {
    color: white;
    font-size: 2em;
    width: 0.5em;
    height: 0.5em;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
    cursor: pointer;
    background: #73ff73;
    border-radius: 10px;
    box-shadow: 1px 1px 1px #47a947;
    margin: 20px auto 0;
  }

  .ToDo-Add:hover {
    box-shadow: none;
    margin-top: 21px;
    margin-left: calc(auto + 1px);
  }

  .ToDo-Container {
    width: 80%;
    margin: 0 auto;
  }

  input {
    width: 60%;
    padding: 10px;
    font-size: 1em;
    margin: 10px auto;
    box-shadow: 1px 3px 20px 0 rgba(0, 0, 0, 0.3)
  }
</style>
