<template>
    <div class="peopleList" style="overflow-x: auto">
        <vheader>
            <span slot="title" class="title">人员管理</span>
        </vheader>
        <router-link to="/AddPeople">
          <el-button type="danger" icon="el-icon-plus" class="addpeople" size='mini'>添加用户</el-button>
        </router-link>
        <div class="table-box">
          <div class="top">
            <div class="action">
              <a href="javascript:;"><i class="icon import_normal"></i>导入用户</a>
              <a href="javascript:;"><i class="icon template_normal"></i>模板下载</a>
            </div>
            <div class="search">
             <el-input placeholder="请输入关键字" v-model="input5" class="input-with-select">
                 <el-select v-model="select" slot="prepend" placeholder="请选择">
                  <el-option label="显示名" value="1"></el-option>
                  <el-option label="组别" value="2"></el-option>
                  <el-option label="类型" value="3"></el-option>
                  </el-select>
                <el-button slot="append" icon="el-icon-search"></el-button>
              </el-input>
            </div>
          </div>
          <div>
            <el-table :data="tableData" style="width: 100%">
              <el-table-column prop="date" label="账号" ></el-table-column>
              <el-table-column  prop="name" label="显示名" ></el-table-column>
              <el-table-column prop="address" label="组别"></el-table-column>
              <el-table-column prop="time" label="创建时间"></el-table-column>
              <el-table-column prop="type" label="类型"></el-table-column>
              <el-table-column prop="note" label="备注"></el-table-column>
              <el-table-column label="操作">
                <template slot-scope="scope">
                  <el-button
                    size="mini"
                    @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
                  <el-button
                    size="mini"
                    type="danger"
                    @click="handleDelete(scope.$index, scope.row)">删除</el-button>
                </template>
              </el-table-column>
            </el-table>
            <el-dialog title="" :visible.sync="dialogFormVisible" center width='350px'  top='40vh'>
                <span>确定要删除吗？</span>
                <div slot="footer" class="dialog-footer">
                  <el-button type="danger" @click="dialogFormVisible = false" size='medium'>完成</el-button>
                  <el-button @click="dialogFormVisible = false" size='medium'>取 消</el-button>
                </div>
              </el-dialog>
          </div>
        </div>
        <div class="paging">
          <el-pagination
            layout="prev, pager, next"
            :total="50">
          </el-pagination>
        </div>
        <el-dialog title="详情" width='386px' top='0' :visible.sync="dialogTableVisible">
            Java大牛带你从0到上线开发企业级电商项目Java大牛带你从0到上线开发企业级电商项目Java大牛带你从0到上线开发企业级电商项目
        </el-dialog>
    </div>
</template>
<script>
import vheader from 'components/vheader'
export default {
  data () {
    return {
      dialogTableVisible: false,
      dialogFormVisible: false,
      input5: '',
      select: '显示名',
      tableData: [{
        date: 'admin',
        name: 'admin',
        address: '杭州小组',
        time: '2018.05.31',
        type: '管理员',
        note: '备注内容',
        operation: '操作'
      }]
    }
  },
  methods: {
    handleEdit (index, row) {
      this.$router.push('/edit/' + index)
      console.log(index, row)
    },
    handleDelete (index, row) {
      this.dialogFormVisible = true
      console.log(index, row)
    }
  },
  components: {
    vheader
  }
}
</script>
<style lang='less' scoped>
.peopleList /deep/ .el-button--danger{
  background: #AB1D29;
  border:1px solid #AB1D29;
}
.peopleList /deep/.el-input-group__prepend .el-input {
    width: 90px;
  }
 .peopleList /deep/ .el-input__inner{
   width: 130px;
 }
.peopleList /deep/ .input-with-select .el-input-group__prepend {
    background-color: #fff;
  }
  .peopleList /deep/ .search .el-button--default{
    background: #AB1D29;
    border-top-left-radius: 0;
    border-bottom-left-radius: 0;
    color: #fff;
    border:1px solid #AB1D29;
  }
  .peopleList /deep/.el-table th {
        background-color: #F5F2EF;
  }
 .peopleList /deep/ .el-dialog__body{
   font-size: 16px;
   text-align: center;
 }
.peopleList{
  .addpeople{
    position: absolute;
    top:15px;
    right: 15px;
  }
  .table-box{
    .top{
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 60px;
      .action{
        a{
          color: #282828;
          margin-right: 20px;
        }
      }
      .icon{
        font-size: 14px;
        display: inline-block;
        width: 19px;
        height: 19px;
        vertical-align: middle;
        margin-right: 8px;
        &.import_normal{
          background: url('../../assets/images/import_normal.png')
        }
        &.template_normal{
           background: url('../../assets/images/template_normal.png')
        }
      }
      .search{

        margin-right: 15px;
      }
    }
  }
  .paging{
    position: fixed;
    left: 0;
    width: 100%;
    text-align: center;
    bottom: 56px;
  }
}

</style>
