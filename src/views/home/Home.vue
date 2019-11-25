<template>
  <div class="home">
      <el-container>
        <el-aside width="200px">
          <todo-menu :menuTab="todoData" @my-event="changeIndex" @add-menu="addMenu"></todo-menu>
        </el-aside>
        <el-main>
          <todo-table :tableMenu="tableData" :tableIndex="index" @index-data="indexData"></todo-table>
        </el-main>
        <!-- <button @click="addlocalstorage">添加</button> -->
      </el-container>
  </div>
</template>

<script>
import Menu from './componse/HomeMemu'
import Table from './componse/HomeTable'
export default {
  data () {
    return {
      todoData: [],
      index: 0,
      tableData: []
      // todo: [
      //   {
      //     name: 'Tany',
      //     list: [
      //       {
      //         mome: '11111111111',
      //         check: false
      //       },
      //       {
      //         mome: '22222222222',
      //         check: false
      //       },
      //       {
      //         mome: '333333333',
      //         check: true
      //       },
      //       {
      //         mome: '4444444',
      //         check: true
      //       }
      //     ]
      //   },
      //   {
      //     name: 'manner',
      //     list: [
      //       {
      //         mome: 'i了解了世界里附近',
      //         check: false
      //       },
      //       {
      //         mome: '可是打开后付款后',
      //         check: false
      //       },
      //       {
      //         mome: '好卡刷卡后付款',
      //         check: true
      //       },
      //       {
      //         mome: '客户机收快递费',
      //         check: true
      //       }
      //     ]
      //   },
      //   {
      //     name: 'zhouwulong',
      //     list: [
      //       {
      //         mome: '和恐惧了空间发链接了',
      //         check: false
      //       },
      //       {
      //         mome: 'UI时代感和覅hi方式待会付款了',
      //         check: false
      //       },
      //       {
      //         mome: 'is大；垃圾卡了',
      //         check: true
      //       },
      //       {
      //         mome: '欧风街管理经费的了解了',
      //         check: true
      //       }
      //     ]
      //   }
      // ]
    }
  },
  components: {
    'todo-menu': Menu,
    'todo-table': Table
  },
  watch: {
    todoData: function (data) {
      console.log('data: ', data)
      localStorage.setItem('todo', JSON.stringify(data))
    }
  },
  methods: {
    initialData () {
      // this.todoData = JSON.parse(localStorage.getItem('memo'))
      let arr = JSON.parse(localStorage.getItem('todo'))
      if (arr) {
        this.todoData = arr
        this.tableData = this.todoData[this.index]
      }
    },
    changeIndex (index) {
      console.log(index)
      this.index = index
      console.log('this.index = index: ', this.index = index)
      this.tableData = this.todoData[this.index]
      console.log('this.tableData = this.todoData[this.index]: ', this.tableData = this.todoData[this.index])
    },
    addMenu (menuNewData) {
      this.todoData = menuNewData
      // console.log(menuNewData)
      // localStorage.setItem()
    },
    indexData (tableList) {
      this.todoData[this.index] = tableList
      this.todoData = Array.from(this.todoData)
    }
    // addlocalstorage () {
    //   localStorage.setItem('todo', JSON.stringify(this.todo))
    // }
  },
  mounted () {
    this.initialData()
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
.nemu-list-add{
  color: #5da5e7;
  border-bottom: 1px solid #908d8d;
}
</style>
