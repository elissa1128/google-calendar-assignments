<script>
import Datepicker from 'vuejs-datepicker';
export default {
  props: ['todoData'],
  components: {
    Datepicker,
  },
  data(){
    return {
      isActive: false,
      datepickerOption: {
        format: 'yyyy-MM-dd',
        placeholder: '請輸入日期',
        inputClass: 'datepicker_date',
        wrapperClass: 'datepicker_wrap',
      },
    }
  },
  methods: {
    open(){
      this.isActive = !this.isActive;
    },
    edit(event){
      event.target.classList.add('editing');
    },
    stopEdit(event){
      event.target.classList.remove('editing');
    },
    removeTodo(){
      this.$emit('remove');
    },
  },
}
</script>

<template>
  <div class="todo_item">
    <div class="todo_header">
      <div class="todo_date">
        <datepicker 
          :format="this.datepickerOption.format"
          :placeholder="this.datepickerOption.placeholder"
          :input-class="this.datepickerOption.inputClass"
          :wrapper-class="this.datepickerOption.wrapperClass"
        v-model="todoData.start">
        </datepicker>
        <!-- <input type="date" 
          class="date"
          v-model="todoData.start" /> -->
        <button type="button" class="btn_remove" @click="removeTodo()"></button>
      </div>
      <div class="todo_title">
        <input type="text" 
          class="title"
          @focus="edit($event)"
          @blur="stopEdit($event)" 
          @keyup.enter="stopEdit($event)"
          v-model="todoData.summary" />
        <button type="button" 
          :class="{btn_create: true,open: this.isActive}" 
          @click="open" 
          v-if="todoData.description">
        </button>
      </div>
    </div>
    <div class="todo_summary" v-if="this.isActive">
      <textarea 
      @focus="edit($event)"
      @blur="stopEdit($event)"
      v-model="todoData.description"></textarea>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "./src/scss/_var.scss";
.todo_item {
  background-color: #fff;
  border-radius: 3px;
  box-shadow: 1px 2px 1px $border-color;
  & + .todo_item {
    margin-top: 10px;
  }
}

input {
  border: none;
  box-sizing: border-box;
  &:focus {
    outline: none;
  }
  &.editing {
    border-bottom: solid 1px $main-color;
  }
}

textarea {
  width: 100%;
  height: 100%;
  min-height: 100px;
  border: none;
  resize: none;
  overflow: auto;
  box-sizing: border-box;
  &:focus {
    outline: none;
  }
  &.editing {
    border: solid 1px $main-color;
  }
}

.todo_header {
  padding: 5px 10px;
  box-sizing: border-box;

  .todo_date {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .todo_title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    .title {
      width: calc(100% - 20px);
      font-size: 16px;
      height: 25px;
      line-height: 25px;
    }
  }
}

.btn_create,.btn_remove,.btn_edit {
  width: 15px;
  height: 15px;
  background-position: center center;
  background-repeat: no-repeat;
  border: none;
  background-color: transparent;
  padding: 0px;
  cursor: pointer;
  &:focus {
    outline: none;
  }
}

.btn_create {
  background-image: url("./../../images/arrow.png");
  background-size: cover;
  transition: transform .5s;
  &.open {
    transform: rotate(180deg);
  }
}

.btn_edit {
  background-image: url("./../../images/edit.png");
  background-size: cover;
  margin-right: 5px;
}

.btn_remove {
  background-image: url("./../../images/remove.png");
  background-size: auto 100%;
}

.todo_summary {
  padding: 0px 10px 10px 10px;
  box-sizing: border-box;
  p {
    line-height: 1.5;
  }
}
</style>


