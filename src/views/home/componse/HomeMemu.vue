<template>
  <div>
    <div class="nemu">
      <p class="nemu-list clearfloat"><span class="nemu-span-icon"><i class="icon iconfont icon-suo"></i></span><a class="nemu-name">tomy</a><span class="nemu-number">0</span></p>
      <p class="nemu-list clearfloat"><span class="nemu-span-icon"><i class="icon iconfont icon-suo"></i></span><a class="nemu-name">tomy</a><span class="nemu-number">0</span></p>
      <p class="nemu-list clearfloat"><span class="nemu-span-icon"><i class="icon iconfont icon-suo"></i></span><a class="nemu-name">tomy</a><span class="nemu-number">0</span></p>
      <p class="nemu-list clearfloat"><span class="nemu-span-icon"><i class="icon iconfont icon-suo"></i></span><a class="nemu-name">tomy</a><span class="nemu-number">0</span></p>
    </div>
    <p class="nemu-list-add"><span class="nemu-span-icon"><i class="el-icon-plus"></i></span><a class="nemu-add">添加</a></p>
  </div>
</template>

<script>
export default {
  name: 'nemu',
  data () {
    return {}
  },
  components: {}
}
</script>

<style scoped lang="less">
.nemu-list{
  height: 50px;
  line-height: 50px;
  border-bottom: 1px solid #908d8d;
  color: #b8b4b4;
  cursor:pointer;

  &:hover {
    color: #fff;

    .nemu-number{
      background-color: #2cc5d2;
    }
  }

  &-add{
    color: #5da5e7;
    border-bottom: 1px solid #908d8d;
  }
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
</style>
