<template>
  <div>
    <div class="main-color btn" v-for="(item, index) of list.type" :key="index">{{item}}</div>
  </div>
</template>
<script>
export default {
  name: 'Type',
  props: {
    list:Object
  }
}
</script>
<style scoped>
  div{
    display: inline-block;
  }
  .btn{
    display: inline-block;
    width: 30px;
    height: 30px;
    line-height: 30px;
    text-align: center;
    cursor: pointer;
    margin: 0 5px;
  }
    .main-color{
    background: #eee;
    color: #ffffff
  }
</style>
