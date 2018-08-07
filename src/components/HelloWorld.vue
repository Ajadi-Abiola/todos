<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="form-group">
      <label for="todo">Enter your ToDos here: </label>
      <div class="container">
        <div class="row">
          <div class="col-md-2">
          </div>
          <div class="col-md-4">
            <input type="text" class="form-control" id="todo" v-model="todoList.input_val"/>
          </div>
          <div class="col-md-2">
            <input type="time" class="form-control" id="time" v-model="todoList.input_time"/>
          </div>
          <div class="col-md-4">
            <button class="btn btn-primary" @click="addToList()">Add to list</button>
          </div>
        </div>
      </div>
    </div>
    <ul v-for="(lists, i) in mainToDoList" :key="i">
      <li>{{lists.input_val}}  at  {{lists.input_time}}</li>
      <button class="btn btn-danger btn-sm" @click="removeFromList(i)">Remove</button>
    </ul>
    <h3>{{ input_val }}</h3>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
    data() {
      return {
        msg: 'To do list',
        input_val: '',
        todoList: {input_val: "", input_time: ""},
        mainToDoList: []
      }
    },
    methods: {
      addToList() {
        let items = {
          input_val: this.todoList.input_val,
          input_time: this.todoList.input_time
        }
        this.mainToDoList.push(items)
      },
      removeFromList(index) {
        this.mainToDoList.splice(index, 1)
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
