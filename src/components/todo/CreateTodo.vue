<script>
import moment from 'moment';
import Datepicker from 'vuejs-datepicker';

export default {
  components: {
    Datepicker,
  },
  data(){
    return {
      task: {
        start: '',
        summary: '',
        description: '',
      },
      datepickerOption: {
        format: 'yyyy-MM-dd',
        placeholder: '請輸入日期',
        inputClass: 'datepicker_date',
        wrapperClass: 'datepicker_wrap',
      }
    }
  },
  methods: {
    onSubmit(){
      if(!moment(this.task.start).isValid() || this.task.summary === ''){
        alert("日期、主題，請填寫完整");
        return;
      }
      this.$emit('submit',this.task);
      this.task = {
        start: '',
        summary: '',
        description: '',
      };
    }
  },
}
</script>

<template>
  <form @submit.prevent="onSubmit">
    <div class="create_header">
      <datepicker 
        :format="this.datepickerOption.format"
        :placeholder="this.datepickerOption.placeholder"
        :clear-button="true"
        :input-class="this.datepickerOption.inputClass"
        :wrapper-class="this.datepickerOption.wrapperClass"
        v-model="task.start">
      </datepicker>
      <input type="text" placeholder="主題" class="name" v-model="task.summary"/>
    </div>
    <textarea placeholder="摘要" v-model="task.description"></textarea>
    <button type="submit">送出</button>
  </form>
</template>

<style lang="scss" scoped>
@import './src/scss/_var.scss';
form {
  width: 100%;
  margin-bottom: 25px;
}

input,textarea {
  padding: 5px 10px;
  box-sizing: border-box;
  &:focus {
    outline: none;
    border: solid 1px $main-color;
  }
}

textarea {
  width: 100%;
  height: 100px;
  margin-bottom: 10px;
  resize: none;
}

button {
  border: none;
  background-color: $main-color;
  color: #fff;
  text-align: center;
  width: 50px;
  height: 30px;
  box-sizing: border-box;
  cursor: pointer;
  &:focus {
    outline: none;
  }
}

.create_header {
  display: flex;
  width: 100%;
  margin-bottom: 10px;
  .name {
    width: 50%;
    height: 35px;
  }
}
</style>


