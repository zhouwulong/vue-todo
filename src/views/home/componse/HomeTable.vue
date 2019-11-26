<template>
  <div class="table-box">
    <div class="table-head">
      <div class="clearfloat">
        <div class="table-head-left">
          <a class="head-left-name">{{this.tableMenu.name}}</a>
          <span class="head-left-number">0</span>
        </div>
        <div class="table-head-right">
          <i class="icon iconfont icon-suo" :class="{dispalyText:guanIcon}" @click="colenIcon"></i>
          <i class="icon iconfont icon-kaisuo" :class="{dispalyText:kaiIcon}" @click="openIcon"></i>
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
          <!-- 开始 -->
          <template slot-scope="scope">
            <el-checkbox
              v-model="scope.row.check"
              @change="clickChange(scope.row.check,scope.$index)"
            ></el-checkbox>
          </template>
          <!-- 结束 -->
        </el-table-column>
        <el-table-column label="备忘语">
          <template slot-scope="scope">
            <span style="margin-right:20px" :class="{classred:scope.row.check}" v-show="scope.$index != modifyindex">{{scope.row.mome}}</span>
            <input style="margin-right:20px;width:auto" class="inputMemo" v-model="scope.row.mome" type="text" v-show="scope.$index == modifyindex" />
            <el-link
              @click="editLink(scope.row,scope.$index)"
              v-if="!scope.row.check && scope.$index != modifyindex"
              class="leftMmargin"
              icon="el-icon-edit"
            ></el-link>
            <el-button type="primary" size="mini" v-show="scope.$index == modifyindex" @click="determineBtn(scope.row)">确定</el-button>
          </template>
        </el-table-column>
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
  data () {
    return {
      dataMemoinput: '',
      checked: '',
      current: false,
      displayTxt: true,
      kaiIcon: false,
      guanIcon: true,
      modifyInput: '',
      modifyindex: null
    }
  },
  watch: {
    'tableMenu.list': function (data) {
      this.$emit('index-data', this.tableMenu)
    }
  },
  props: ['tableMenu', 'tableIndex'],
  methods: {
    initial () {
      // console.log(this.tableMenu.list)
      // for (var i = 0; i < this.tableMenu.list.length; i++) {
      // console.log('this.tableMenu.list[i].check: ', this.tableMenu.list[i].check)
      // if (this.tableMenu.list[i].check !== false) {
      //   this.guanIcon = false
      // }
      // }
    },
    editLink (row, index) {
      console.log(row)
      // $event.displayTxt = row.check
      this.modifyindex = index
      console.log('this.modifyindex : ', this.modifyindex)
    },
    clickChange (check, index) {
      console.log('check: ', check)
      this.current = index
      this.tableMenu.list = Array.from(this.tableMenu.list)
    },
    handleDelete (index, row) {
      this.tableMenu.list.splice(index, 1)
      // this.tableMenu.list = Array.from(this.tableMenu.list)
      console.log('this.tableMenu.list: ', this.tableMenu.list)
    },
    openIcon () {
      this.kaiIcon = true
      this.guanIcon = false
      // console.log(this.tableMenu.list.check)
      for (var i = 0; i < this.tableMenu.list.length; i++) {
        this.tableMenu.list[i].check = true
        this.tableMenu.list = Array.from(this.tableMenu.list)
      }
    },
    determineBtn (row) {
      this.modifyindex = null
      console.log('this.modifyindex: ', this.modifyindex)
      // this.modifyindex = row.mome
      this.tableMenu.list = Array.from(this.tableMenu.list)
    },
    colenIcon () {
      this.kaiIcon = false
      this.guanIcon = true
      for (var i = 0; i < this.tableMenu.list.length; i++) {
        this.tableMenu.list[i].check = false
        this.tableMenu.list = Array.from(this.tableMenu.list)
      }
    },
    addData () {
      if (this.dataMemoinput === '') {
        this.$message({
          message: '输入框不能为空',
          type: 'warning',
          center: true,
          offset: 300
        })
      } else {
        this.tableMenu.list.push({ check: false, mome: this.dataMemoinput })
        // console.log("this.tableMenu.list: ", this.tableMenu.list);
        // this.tableMenu.list = Array.from(this.tableMenu.list)
      }
    }
    // 开始
    // 结束
  },
  updated () {
    for (var i = 0; i < this.tableMenu.list.length; i++) {
      if (this.tableMenu.list[i].check !== false) {
        this.guanIcon = false
        this.kaiIcon = true
      }
    }
  },
  mounted () {},
  components: {}
}
</script>

<style scoped lang="less">
// .table-head div:nth-of-type(1){
//     height: 50px;
//     line-height: 50px;
// }
.inputMemo{
  border: none;
  height: 25px;
  border-bottom:1px solid #ddd;
}
.leftMargin {
  margin-left: 20px;
}
.dispalyText {
  display: none;
}
.classred {
  text-decoration: line-through;
}
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
    .icon-suo,
    .icon-kaisuo {
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
