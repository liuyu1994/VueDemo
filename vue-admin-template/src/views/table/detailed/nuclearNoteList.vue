<template>
  <div style="margin-left: 2%">
    <br>
    <el-divider content-position="left">料件详情</el-divider>
    <br>
    <el-divider content-position="left">核扣历史详情</el-divider>
    <el-table
      :data="tableData"
      border
      style="width: 100%">
      <el-table-column
        prop="a1"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: 'NuclearNoteList',
  data() {
    return {
      a1: '',
      id: '0',
      tableData: [{
        a1: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        a1: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄'
      }, {
        a1: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄'
      }, {
        a1: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄'
      }]
    }
  },
  created() {
    //params 二级菜单刷新无值
    this.id = this.$route.query.id
    console.log(this.id)
  }
}
</script>

<style scoped>

</style>
