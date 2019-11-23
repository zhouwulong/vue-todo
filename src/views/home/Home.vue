<template>
  <div class="home">
      <el-container>
        <el-aside width="200px">
          <todo-menu></todo-menu>
        </el-aside>
        <el-main>
          <todo-table/>
        </el-main>
      </el-container>
  </div>
</template>

<script>
import Menu from './componse/HomeMemu'
import Table from './componse/HomeTable'
export default {
  components: {
    'todo-menu': Menu,
    'todo-table': Table
  }
}
</script>

<style lang="less" scoped>
.home{
  width: 80%;
  margin: 0 auto;
}
.nemu-list{
  height: 50px;
  line-height: 50px;
  border-bottom: 1px solid #908d8d;
  color: #b8b4b4;
  cursor:pointer;
}
.nemu-list:hover{
  color: #fff;
}
.nemu-list:hover .nemu-number{
   background-color: #2cc5d2;
}
.nemu-span-icon{
  display: inline-block;
  width: 40px;
  height: 50px;
  text-align: center
}
.nemu-number{
  float: right;
  margin-right: 15px;
  display: inline-block;
  width: 20px;
  height: 20px;
  line-height: 20px;
  text-align: center;
  border-radius: 50%;
  background-color: #60758d;
  margin-top: 15px;
}
.nemu-list-add{
  color: #5da5e7;
  border-bottom: 1px solid #908d8d;
}
</style>
