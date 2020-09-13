<template>
  <div style="margin-left: 2%">
    <br>
    <el-divider content-position="left">查询条件</el-divider>
    <br>
    <el-form :inline="true" :model="searchMap" class="demo-form-inline">
      <el-form-item label=" 可查询企业 ">
        <el-select v-model="searchMap.user" placeholder="" clearable>
          <el-option label="企业1" value="shanghai"></el-option>
          <el-option label="企业2" value="beijing"></el-option>
          <el-option label="企业3" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="料号">
        <el-input v-model="searchMap.user" placeholder="料号" clearable></el-input>
      </el-form-item>
      <el-form-item label="底账编号">
        <el-input v-model="searchMap.region" placeholder="底账编号" clearable>
        </el-input>
      </el-form-item>
      <br>
      <el-form-item label="经营企业名称">
        <el-input v-model="searchMap.user" placeholder="经营企业名称"></el-input>
      </el-form-item>
      <el-form-item label="物料类型">
        <el-select v-model="searchMap.user" placeholder="物料类型">
          <el-option label="全部" value="shanghai"></el-option>
          <el-option label="A-原料" value="beijing"></el-option>
          <el-option label="B-半成品" value="be1ijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="经营企业名称">
        <el-input v-model="searchMap.user" placeholder="经营企业名称"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">查询</el-button>
        <el-button type="primary" @click="onReset">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import {getList} from "@/api/table";

export default {
  name: 'storeHouseQuery',
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
      list: [],
      total: 0,//总记录数
      currentPage: 1,//当前页
      pageSize: 10,//每页大小
    }
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

<style scoped>
.el-form-item label:after {
  content: "";
  display: inline-block;
  width: 100%;
}

.el-form-item__label {
  text-align: justify;
  height: 50px;
}

.el-form-item.is-required .el-form-item__label:before {
  content: none !important;
}
</style>
