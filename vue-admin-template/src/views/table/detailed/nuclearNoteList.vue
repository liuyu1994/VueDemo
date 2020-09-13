<template>
  <div style="margin-left: 2%">
    <br>
    <el-divider content-position="left">料件详情</el-divider>
    <el-table
      :data="headTableData"
      border
      style="width: 100%">
      <el-table-column
        prop="a1"
        label="物料类型"
        width="180"
        align="center">
      </el-table-column>
      <el-table-column
        prop="name"
        label="料号"
        width="180"
        align="center">
      </el-table-column>
      <el-table-column
        prop="address"
        label="中文名称"
        align="center">
      </el-table-column>
      <el-table-column
        prop="address"
        label="商品编码"
        align="center">
      </el-table-column>
      <el-table-column
        prop="address"
        label="计量单位"
        align="center">
      </el-table-column>
      <el-table-column
        prop="address"
        label="规格型号"
        align="center">
      </el-table-column>
      <el-table-column
        prop="address"
        label="申报币制"
        align="center">
      </el-table-column>
      <el-table-column
        prop="address"
        label="核注清单库存"
        align="center">
      </el-table-column>
    </el-table>
    <br>
    <el-divider content-position="left">核扣历史详情</el-divider>
    <el-table
      :data="tableData"
      border
      style="width: 100%">
      <el-table-column label="核注清单库存核扣单据" align="center">
        <el-table-column
          prop="id"
          label="序号"
          align="center">
          <template slot-scope="scope">
            {{scope.$index+1}}
          </template>
        </el-table-column>
        <el-table-column
          prop="date"
          label="增加标记"
          align="center">
        </el-table-column>
        <el-table-column
          prop="name"
          label="单据号"
          align="center">
        </el-table-column>
        <el-table-column
          prop="address"
          label="单据类型"
          align="center">
        </el-table-column>
        <el-table-column
          prop="address"
          label="物料流向"
          align="center">
        </el-table-column>
        <el-table-column
          prop="address"
          label="表体号"
          align="center">
        </el-table-column>
      </el-table-column>
      <el-table-column label="核扣明细" align="center">
        <el-table-column
          prop="a1"
          label="前次结余"
          align="center"
          width="110">
        </el-table-column>
        <el-table-column
          prop="address"
          label="本次核扣"
          align="center">
        </el-table-column>
        <el-table-column
          prop="address"
          label="本次核扣"
          align="center">
        </el-table-column>
        <el-table-column
          prop="address"
          label="核扣时间"
          align="center">
        </el-table-column>
      </el-table-column>
    </el-table>
    <el-pagination
      @size-change="fetchData"
      @current-change="fetchData"
      :current-page="currentPage"
      :page-sizes="[5,10,20]"
      :page-size="10"
      layout="total, sizes, prev, pager, next, jumper"
      :total="total">
    </el-pagination>
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
        date: '减',
        a1: '2016-05-02',
        name: '王小虎',
        address: '2000'
      }, {
        a1: '2016-05-04',
        name: '王小虎',
        address: '2000'
      }, {
        a1: '2016-05-01',
        name: '王小虎',
        address: '2000'
      }, {
        a1: '2016-05-03',
        name: '王小虎',
        address: '2000'
      }],
      headTableData: [{
        a1: '原料',
        name: '10001',
        address: '100'
      }],
      list:[],
      total: 0,//总记录数
      currentPage: 1,//当前页
      pageSize: 10,//每页大小
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
