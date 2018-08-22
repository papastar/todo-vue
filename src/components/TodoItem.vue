<template>
  <div class="TodoItem">
    <p class="TodoItem-Text">{{todo.text}}</p>
    <div class="TodoItem-Delete"
         @click="deleteItem(todo)">-
    </div>
  </div>
</template>

<script>
  export default {
    name: "TodoItem",
    props: ['todo'],
    methods: {
      deleteItem(todo) {
        this.$emit('delete', todo)
      }

    }
  }
</script>

<style scoped>
  .TodoItem {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .TodoItem-Text {
    width: 90%;
    background-color: white;
    border: 1px solid lightgrey;
    box-shadow: 1px 1px 1px lightgrey;
    padding: 12px;
    margin-right: 10px;
  }
  .TodoItem-Delete {
    width: 20px;
    padding: 5px;
    height: 20px;
    cursor: pointer;
    background: #ff7373;
    border-radius: 10px;
    box-shadow: 1px 1px 1px #c70202;
    color: white;
    font-size: 18px;
    margin-right: 5px;
  }
  .TodoItem-Delete:hover {
    box-shadow: none;
    margin-top: 1px;
    margin-left: 1px;
  }



</style>
