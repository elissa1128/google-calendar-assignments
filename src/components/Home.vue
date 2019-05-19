<script>
import Todo from './todo/Todo';

export default {
  components: {
    Todo,
  }
}
</script>


<template>
<div class="wrap">
  <Todo></Todo>
</div>
</template>

<style lang="scss" scoped>
@import './src/scss/_var.scss';
.wrap {
  max-width: $container;
  width: 50%;
  height: 100%;
  margin: 0 auto;
  position: relative;
  @media screen and (max-width: $pad){
    width: 100%;
    height: auto;
    padding: 0px 20px;
    box-sizing: border-box;
  }
}
</style>

