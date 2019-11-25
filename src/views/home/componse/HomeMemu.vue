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
        <i class="el-icon-plus"></i>
      </span>
      <a class="nemu-add" @click="adduser">添加</a>
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
      index: 0
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
      this.menuTab.push({ name: 'newList', list: [] })
      // this.menuTab
      this.$emit('add-menu', this.menuTab)
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
