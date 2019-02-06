<template>
  <div class="jumbotron">
       <router-link to="/about">About</router-link>
    <h1>Hello {{msg}} Todo list </h1>
    <form>
    <div class="form-group">
      <div class="col-lg-3"></div>
    <div ><input class="col-lg-3" type="text" placeholder="Add Tasks" v-model="input" id="task"></div>
    <div class="col-lg-6">

      <button @click="add" @keyup.enter="add" class="btn btn-primary">Add</button>
    </div>
    </div>
  </form>
     <div v-for="(ar, index) in arr">
      <input type="checkbox" name="check" @change="changeEvent(index, ar.done)">
        <span :class="{done: ar.done}">{{ar.text}} </span><button @click="deleteTodo(index)"><i class="fa fa-trash"></i></button>
        <button @click="editTodo(ar)">edit</button>

     </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      arr: [{text:"", done:false}],
      id: 0,
     input: ""
    }
  },
  methods: {
    add(){
      if(this.input.length != 0){
      this.arr.push({text:this.input, done:false}),
       this.input= ""

    }
  },
    deleteTodo(event){
         this.arr.splice(event, 1);
     },
     editTodo(event){
      this.input = event
     },
     editIt(event){

       this.arr[event] = this.input
     },
     changeEvent(index, val){
       this.arr[index].done = !val
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
  color: green;
}
.done{
  text-decoration-line: line-through;
  color:green;
}
</style>
