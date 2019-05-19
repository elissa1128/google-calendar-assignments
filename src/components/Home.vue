<script>
import axios from 'axios';
import moment from 'moment';
import CreateTodo from './todo/CreateTodo';
import TodoItem from './todo/TodoItem';
const API_KEY = 'AIzaSyD_QB8TICtDpFgWMv2es_oDR2NPYYLQ7Po';

export default {
  components: {
    CreateTodo,
    TodoItem,
  },
  data(){
    return {
      todoItems: [],
      formatData: [],
    }
  },
  methods: {
    getCalendar(){
      axios.get(`https://www.googleapis.com/calendar/v3/calendars/tjhnbpdgbd9t04dqkg4pemlvj4@group.calendar.google.com/events?key=${API_KEY}`)
      .then((result)=>{
        let newArray = result.data.items;
        this.format(newArray);
      });
    },
    format(newArray){
      newArray.forEach((elem,idx)=>{
        this.formatData = {
          start: elem.start.date,
          summary: elem.summary,
          description: elem.description,
        }
        this.todoItems.push(this.formatData);
      });
    },
    onSubmit(task){
      let newArray = this.todoItems;
      newArray.push(task);
    },
    removeTodo(idx){
      let newArray = this.todoItems;
      newArray.splice(idx,1);
    }
  },
  mounted(){
    this.getCalendar();
  },
}
</script>

<template>
  <div class="todo_content">
    <h3>待辦事項</h3>
    <CreateTodo @submit="onSubmit"></CreateTodo>
    <TodoItem 
      v-for="(item,idx) in todoItems" :key="idx" 
      :todoData="item" 
      v-on:remove="removeTodo(idx)">
    </TodoItem>
  </div>
</template>

<style lang="scss" scoped>
@import './src/scss/_var.scss';

.todo_content {
  max-width: $container;
  width: 50%;
  margin: 0 auto;
  padding-top: 40px;
  h3 {
    font-size: 20px;
    margin-bottom: 15px;
  }
}
</style>

