<template>
  <div class="jumbotron">
       <router-link to="/about">About</router-link>
    <h1>Hello {{msg}} Todo list </h1>
    <form>
    <div class="form-group">
      <div class="col-lg-3"></div>
    <div ><input class="col-lg-3" type="text" placeholder="Add Tasks" v-model="input" id="task"></div>
    <div class="col-lg-6"><button @click="add" @keyup.enter="add" class="btn btn-primary">Add</button>

    </div>
    </div>
  </form>
     <div v-for="(ar, index) in arr">
        <span id="try">{{ar}} </span><button @click="deleteTodo(index)"><i class="fa fa-trash"></i></button>
        <button @click="editTodo(ar)">edit</button>
        <button @click="editIt(index)">editIt</button>
     </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      arr: [],
      id: 0,
     input: ""
    }
  },
  methods: {
    add(){
      if(this.input.length != 0){
      this.arr.push(this.input),
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
</style>
