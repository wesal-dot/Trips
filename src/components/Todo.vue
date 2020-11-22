<template>
  <div class='ui centered card'>
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ todo.title }}
      </div>
      <div class='meta'>
          {{ todo.project }}
      </div>
      <div class='meta'>
          {{ todo.project2 }}
      </div>
      <div class='meta'>
          {{ todo.project3 }}
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Trip</label>
          <input type='text' v-model="todo.title" >
        </div>
        <div class='field'>
          <label>Travel</label>
          <input type='date' v-model="todo.project">
          <label>Return</label>
          <input type='date' v-model="todo.project2">
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
 
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-show="!isEditing &&todo.done" disabled>
        Completed
    </div>
    <div class='ui bottom attached red basic button' v-on:click="completeTodo(todo)" v-show="!isEditing && !todo.done">
        Pending
    </div>
  </div>
</template>

<script type="text/javascript">
//import CreateTodo from './components/CreateTodo';
  export default {
    props: ['todo'], 
    data() {
      return {
        isEditing: false,
          
      };
    },
    methods: {
      completeTodo(todo) {
        this.$emit('complete-todo', todo);
      },
      deleteTodo(todo) {
        this.$emit('delete-todo', todo);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
   //let date1=new Date(todo.prject);
     //  let date2=new Date(todo.prject2);
       //todo.project3 =(date2.getTime() - date1.getTime()) /// (1000 * 3600 * 24); 
       //return Difference_In_Time;
      },
     /* calculateDifferenceBetweenDates(d1,d2){
      let date1=new Date(d1);
      let date2=new Date(d2);
        todo.project3 = (date2.getTime() - date1.getTime()) / (1000 * 3600 * 24); 
       return todo.project3;
    },*/
    },
  };
</script>