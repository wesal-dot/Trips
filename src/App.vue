 <template>
  <div id="app">
    <h1 class="ui dividing centered header">Vue.js Todo App</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="createTodo"></create-todo>
       </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert';
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';
export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [{
        title: 'Trip 1',
        project: 'Travel Date',
        project2: 'Return Date',
        project3: 'Number Of Days',


        done: false,
      }, {
        title: 'Todo B',
        project: 'Travel Date',
        project2: 'Return Date',
        project3: 'Number Of Days',
        done: true,
      }, {
        title: 'Todo C',
        project: 'Travel Date',
        project2: 'Return Date',
        project3: 'Number Of Days',
        done: false,
      }, {
        title: 'Todo D',
        project: 'Travel Date',
        project2: 'Return Date',
        project3: 'Number Of Days',
        done: false,
      }],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
      sweetalert('Success!', 'To-Do created!', 'success');
    },
    /*calculateDifferenceBetweenDates(d1,d2){
      let date1=new Date(d1);
      let date2=new Date(d2);
      Difference_In_Time = (date2.getTime() - date1.getTime()) / (1000 * 3600 * 24); 
       return Difference_In_Time;
    },*/
   
  },
};
</script>