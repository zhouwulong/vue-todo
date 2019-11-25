<template>
  <div class="table-box">
    <div class="table-head">
      <div class="clearfloat">
        <div class="table-head-left">
          <a class="head-left-name">anny</a>
          <span class="head-left-number">0</span>
        </div>
        <div class="table-head-right">
          <i class="icon iconfont icon-suo"></i>
          <i class="icon iconfont icon-shanchu"></i>
        </div>
      </div>
      <div>
        <p class="table-head-add">
          <i class="el-icon-plus" @click="addData"></i>
          <input class="table-head-add-input" v-model="dataMemoinput" placeholder="请输入" type="text" />
        </p>
      </div>
    </div>
    <div class="table-zt">
      <el-table :data="tableMenu.list" style="width: 100%" :show-header="false">
        <el-table-column width="35">
        </el-table-column>
        <el-table-column prop="mome" label="备忘语"></el-table-column>
        <el-table-column label="操作" width="150">
          <template slot-scope="scope">
            <el-button size="mini" type="danger" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'todo-tables',
  data () {
    return {
      // multipleSelection: [],
      dataMemoinput: ''
      // msg: '',
    }
  },
  watch: {
    'tableMenu.list': function (data) {
      this.$emit('index-data', this.tableMenu)
    }
  },
  props: [
    'tableMenu',
    'tableIndex'
  ],
  // props: ['table', 'inputName'],
  methods: {
    initial () {
      // console.log('this.tableMenu.list: ', this.tableMenu.list)
      // console.log('this.tableMenu: ', this.tableMenu)
      // this.list = this.tableMenu.list
      // console.log('this.list: ', this.list)
    },
    handleDelete (index, row) {
      this.tableMenu.list.splice(index, 1)
      // this.tableMenu.list = Array.from(this.tableMenu.list)
      console.log('this.tableMenu.list: ', this.tableMenu.list)
    },

    addData () {
      // let memovalue = { memo: this.dataMemoinput }
      // this.tableData.push(memovalue)
      // this.dataMemoinput = ''
      // localStorage.setItem('memo', JSON.stringify(this.tableData))
      // localStorage.getItem('memo')
      this.tableMenu.list.push({ check: false, mome: this.dataMemoinput })
      console.log('this.tableMenu.list: ', this.tableMenu.list)
      // this.tableMenu.list = Array.from(this.tableMenu.list)
    }
  },
  // updated () {
  //   this.initial()
  // },
  mounted () {
    // console.log('this.tableMenu: ', this.tableMenu)
  },
  components: {}
}
</script>

<style scoped lang="less">
// .table-head div:nth-of-type(1){
//     height: 50px;
//     line-height: 50px;
// }
.table-head {
  background: linear-gradient(180deg, #d0edf5, #e1e5f0);
  div:nth-of-type(1) {
    height: 35px;
    line-height: 35px;
  }
  .table-head-left {
    float: left;
    .head-left-name {
      margin-left: 20px;
      font-size: 17px;
      font-weight: 900;
    }
    .head-left-number {
      margin-left: 15px;
      display: inline-block;
      width: 20px;
      height: 20px;
      line-height: 20px;
      border-radius: 50%;
      text-align: center;
      background: #2cc5d2;
      font-size: 12px;
      color: #fff;
    }
  }
  .table-head-right {
    float: right;
    .icon-suo {
      margin-right: 30px;
    }
    .icon-shanchu {
      margin-right: 20px;
    }
  }
  .table-head-add {
    margin: 0;
    height: 35px;
    line-height: 35px;
    .el-icon-plus {
      margin-left: 20px;
      margin-right: 5px;
    }
    .table-head-add-input {
      width: 80%;
      border: none;
      height: 25px;
      padding-left: 5px;
      background: none;
      outline: none;
    }
  }
}
</style>
