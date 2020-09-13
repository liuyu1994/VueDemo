<template>
  <div style="margin-left: 2%">
    <br>
    <el-divider content-position="left">查询条件</el-divider>
    <br>
    <el-form :inline="true" :model="searchMap" class="demo-form-inline">
      <el-form-item label="企业编码">
        <el-input v-model="searchMap.user" placeholder="企业编码" clearable></el-input>
      </el-form-item>
      <el-form-item label="底账编号">
        <el-input v-model="searchMap.user" placeholder="底账编号" clearable></el-input>
      </el-form-item>
      <el-form-item label="库存物料">
        <el-select v-model="searchMap.region" placeholder="库存物料" clearable>
          <el-option label="全部" value="shanghai"></el-option>
          <el-option label="原料" value="beijing"></el-option>
          <el-option label="半成品" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="料号">
        <el-input v-model="searchMap.user" placeholder="料号"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">查询</el-button>
        <el-button type="primary" @click="onReset">重置</el-button>
      </el-form-item>
    </el-form>
    <el-row :gutter="0">
      <el-col :span="24">
        <div class="grid-content bg-purple">
          <el-table
            :data="tableData"
            border
            style="width: 100%">
            <el-table-column label="物料信息" align="center">
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
              label="料号"
              align="center">
            </el-table-column>
            <el-table-column
              prop="name"
              label="项号"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="中文名称"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="HS编码"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="库存物料"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="计量单位"
              align="center">
            </el-table-column>
            </el-table-column>
            <el-table-column label="库存数据" align="center">
            <el-table-column
              prop="a1"
              label="核注清单库存A1"
              align="center"
              width="110">
              <template slot-scope="scope">
                <router-link :to="{name: 'nuclearList', query: { id: scope.row.a1}}">{{scope.row.a1}}</router-link>
              </template>
            </el-table-column>
            <el-table-column
              prop="address"
              label="企业确认库存A2"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="在途库存A3=A1-A2"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="工单折料A4"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="在制库存A5"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="仓储库存A6=A2-A4-A5"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="实盘库存"
              align="center">
            </el-table-column>
            <el-table-column
              prop="address"
              label="实盘时间"
              align="center">
            </el-table-column>
            </el-table-column>
          </el-table>
        </div>
      </el-col>
    </el-row>
    <br/>
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

import { getList } from '@/api/table'

export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        published: 'success',
        draft: 'gray',
        deleted: 'danger'
      }
      return statusMap[status]
    }
  },
  data() {
    return {
      searchMap: {
        user: '',
        region: ''
      },
      tableData: [{
        id: '1',
        date: 'XXXX01',
        name: '王小虎',
        address: '黄金',
        a1: '10'
      }, {
        id: '2',
        date: 'XXXX01',
        name: '王小虎',
        address: '黄金',
        a1: '666'
      }, {
        id: '2',
        date: 'XXXX01',
        name: '王小虎',
        address: '黄金',
        a1: '10'
      }, {
        id: '2',
        date: 'XXXX01',
        name: '王小虎',
        address: '黄金',
        a1: '10'
      }],
      list:[],
      total: 0,//总记录数
      currentPage: 1,//当前页
      pageSize: 10,//每页大小
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      this.listLoading = true
      getList().then(response => {
        this.list = response.data.items
        this.listLoading = false
      })
    },
    onSubmit() {
      console.log('submit!')
    },
    onReset() {
      this.searchMap = {}
    }
  }
}
</script>
<style>
/*自定义表格表头高度和每一行的高度*/
.el-table__header tr,
.el-table__header th {
  padding: 0;
  height: 30px;
  line-height: 50px;
}

.el-table__body tr,
.el-table__body td {
  padding: 0;
  height: 30px;
  line-height: 30px;
}
</style>
