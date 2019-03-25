<template>
  <div>
    <label for="">
      配色方案：<span class="add-btn" @click="add">新增配色方案+</span>
    </label>
    <label for="">
      <ul>
      <span class="scheme-title">方案列表：</span>
      <li v-for="(scheme, index) in schemeList" :key="index">
        <select name="" id="" class="select-btn">
        <option value ="red" v-for="(item, index) of scheme.schemes" :key="index">{{item}}</option>
        </select>
        <type :list="scheme"></type>
        <div class="add-color btn" @click="addType(index)">+</div>
        <div class="sub-color btn" @click="subType(index)">-</div>
        <span  class="del" @click="del(index)">删除</span>
      </li>
    </ul>
    </label>
  </div>
</template>

<script>
import Type from './Type.vue'
export default {
  name: 'Schemes',
  components:{
    Type
  },
  data () {
    return {
      schemeList: [{
        schemes:['蓝色','绿色','灰色'],
        type:['主']
      }, {
        schemes:['蓝色','绿色','灰色'],
        type:['主']
      }]
    }
  },
  methods: {
    add () {
      var item = {schemes:['红色','绿色','灰色'],type:['主']}
      this.schemeList.push(item)
      // this.schemeList = [...this.schemeList, item]
      console.log(this.schemeList)
      // this.$set(this.schemeList,this.schemeList.length,item)
    },
    del (index) {
      if(this.schemeList.length > 1){
        this.schemeList.splice(index,1)
      }
    },
    addType (index) {
      const len = this.schemeList[index].type.length
      this.schemeList[index].type.push(`加${len}`)
    },
    subType (index) {
      if(this.schemeList[index].type.length > 1){
        this.schemeList[index].type.pop()
      }
    }
  },
  watch: {
    schemeList () {
       this.$forceUpdate()
    }
  }
}
</script>

<style scoped>
a{
      text-decoration: none;
    }
    ul li{
      list-style: none;
      margin-left: 80px;
      margin-bottom: 10px;
    }
    ul li:first-child{
      float: left;
      margin-top: 0;
    }
    ul {
      float: left;
    }
  .scheme-title{
    float: left;
    height: 32px;
    line-height: 32px;
  }
 .select-btn{
    padding: 5px 10px;
    width: 150px;
    border-radius: 5px;
  }
  option{
    height: 24px;
    line-height: 24px;
  }
  .btn{
    display: inline-block;
    width: 30px;
    height: 30px;
    line-height: 30px;
    text-align: center;
    cursor: pointer;
    margin: 0 10px;
  }
  .btn:hover{
    border-color:rgb(107, 134, 243);
    color: rgb(107, 134, 243);
  }
  .add-color, .sub-color{
    border: 1px solid #999797;
    color: #999797;
    background: #fff;
  }
  .main-color:hover{
    color: #ffffff;
  }
  .del{
    display: inline-block;
    cursor: pointer;
  }
  .del:hover{
    color: rgb(107, 134, 243);
  }
  .main-color-model li:hover{
    background: #03f;
  }
  .main-color-model{
    width: 100px;
    border: 1px solid #999999;
    background: #ffffff;
  }
  label{
    display: block;
    margin: 10px
   }
  .add-btn{
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
    border: 1px solid #dddddd
  }
  .add-btn:hover{
    border-color:rgb(107, 134, 243);
    color: rgb(107, 134, 243);
  }
</style>
