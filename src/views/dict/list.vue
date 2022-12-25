<script setup>
import {ref} from 'vue'
const tableData=ref([{
  date: '2016-05-02',
  name: '王小虎',
  province: '上海',
  city: '普陀区',
  address: '上海市普陀区金沙江路 1518 弄',
  zip: 200333
}, {
  date: '2016-05-04',
  name: '王小虎',
  province: '上海',
  city: '普陀区',
  address: '上海市普陀区金沙江路 1517 弄',
  zip: 200333
}, {
  date: '2016-05-01',
  name: '王小虎',
  province: '上海',
  city: '普陀区',
  address: '上海市普陀区金沙江路 1519 弄',
  zip: 200333
}, {
  date: '2016-05-03',
  name: '王小虎',
  province: '上海',
  city: '普陀区',
  address: '上海市普陀区金沙江路 1516 弄',
  zip: 200333
}])
const onClickDict=row=>{
  console.log(row)
}
</script>
<template>
  <el-table
    :data="tableData"
    border
    style="width: 100%">
    <el-table-column
      fixed
      prop="date"
      label="编号">
    </el-table-column>
    <el-table-column
      prop="name"
      label="名称">
    </el-table-column>
    <el-table-column
      prop="province"
      label="值">
    </el-table-column>
    <el-table-column
      prop="address"
      label="其他"
     >
    </el-table-column>
  </el-table>
</template>


<style lang="scss" scoped>
.tb-table{
  margin-bottom: 20px;
}
</style>
