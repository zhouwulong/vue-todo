<template>
  <div>
    <div class="nemu">
      <p class="nemu-list clearfloat" v-for="(item,index) in menuTab" :key="index" @click="changeMenuone(index)">
        <span class="nemu-span-icon">
          <i class="icon iconfont icon-suo"></i>
        </span>
        <a class="nemu-name">{{item.name}}</a>
        <span class="nemu-number">{{item.list.length}}</span>
      </p>
    </div>
    <p class="nemu-list-add">
      <span class="nemu-span-icon">
        <i class="el-icon-plus" @click="adduser"></i>
      </span>
      <a class="nemu-add" :class="{displayAdd:memuAdd}" @click="menuAdd">添加</a>
      <input type="text" v-model="inputAdd" class="inputAdd" placeholder="请输入名称" :class="{displayAdd:memuInput}">
    </p>
  </div>
</template>

<script>
export default {
  name: 'nemu',
  props: [
    'menuTab'
  ],
  data () {
    return {
      index: 0,
      memuAdd: false,
      memuInput: true,
      inputAdd: ''
    }
  },
  methods: {
    initialData () {
      // this.todoData = JSON.parse(localStorage.getItem('memo'))
      // let arr = JSON.parse(localStorage.getItem('todo'))
      // if (arr) {
      //   this.todoData = arr
      // }
      // console.log('this.menuTab: ', this.menuTab)
    },
    adduser () {
      if (this.inputAdd === '') {
        this.$message({
          message: '输入框不能为空',
          type: 'warning',
          center: true,
          offset: 300
        })
      } else {
        this.menuTab.push({ name: this.inputAdd, list: [] })
        this.$emit('add-menu', this.menuTab)
        this.memuAdd = false
        this.memuInput = true
      }
    },
    menuAdd () {
      this.memuAdd = true
      this.memuInput = false
    },
    changeMenuone (index) {
      this.index = index
      console.log('this.index: ', this.index)
      this.$emit('my-event', this.index)
    }
  },
  mounted () {
    this.initialData()
  },
  components: {}
}
</script>

<style scoped lang="less">
.displayAdd{
  display: none
}
.inputAdd{
  width: 150px
}
.nemu-list {
  height: 50px;
  line-height: 50px;
  border-bottom: 1px solid #908d8d;
  color: #b8b4b4;
  cursor: pointer;

  &:hover {
    color: #fff;

    .nemu-number {
      background-color: #2cc5d2;
    }
  }

  &-add {
    color: #5da5e7;
    border-bottom: 1px solid #908d8d;
  }
}
.nemu-span-icon {
  display: inline-block;
  width: 40px;
  height: 50px;
  text-align: center;
}
.nemu-number {
  margin-right: 15px;
  display: inline-block;
  width: 20px;
  float: right;
  height: 20px;
  line-height: 20px;
  text-align: center;
  border-radius: 50%;
  background-color: #60758d;
  margin-top: 15px;
}
</style>
