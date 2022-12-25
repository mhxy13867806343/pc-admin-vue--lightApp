<script setup>
import {ref,reactive} from 'vue'
import {useRouter} from 'vue-router'
const router=useRouter()
const search=ref('')
const addDictVisible=ref(false) // 添加字典弹窗
const addChildDictVisible=ref(false)// 添加子字典弹窗
const dataDictForm=reactive({
  "dict_id": '',
  "key_name": "",
  "key_args": "",
  "key_value": "",
  "key_url": ""
}) // 字典数据
const form = reactive({
key:''
})
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
const onAddClickDict=row=>{
  addChildDictVisible.value=true
  dataDictForm.dict_id=row.dict_id
  dataDictForm.key_name=row.key_name
  dataDictForm.key_args=row.key_args
  dataDictForm.key_value=row.key_value
  dataDictForm.key_url=row.key_url
}
const onShowClickDict=row=>{
  router.push({
    path: '/dict-list',
    query: {
      keys: 123
    }
  })
}
</script>
<template>
  <el-button-group class="tb-table">
    <el-input
      placeholder="请输入内容"
      v-model="search" size="small"
      clearable>
    </el-input>
    <el-button type="primary">搜索字典</el-button>
    <el-button type="primary" @click="addDictVisible=true">添加字典</el-button>
  </el-button-group>
  <el-table
    :data="tableData"
    border
    style="width: 100%">
    <el-table-column
      fixed
      prop="date"
      label="编号"
      >
    </el-table-column>
    <el-table-column
      prop="name"
      label="类型">
    </el-table-column>
    <el-table-column
      fixed="right"
      label="操作"
      width="100">
      <template v-slot="{row}">
        <el-button-group>
          <el-button  type="text" size="mini" style="margin-right: 10px" @click="onAddClickDict(row)">添加</el-button>
          <el-button  type="text" size="mini" style="margin-right: 10px" @click="onShowClickDict(row)">查看</el-button>
        </el-button-group>
      </template>
    </el-table-column>
  </el-table>
  <el-dialog v-model="addDictVisible" title="添加">
    <el-form :model="form">
      <el-form-item label="请添加关键字" label-width="140px">
        <el-input v-model="form.key" autocomplete="off" clearable placeholder="请添加关键字(如hot,中文等)"/>
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="addDictVisible = false">取消</el-button>
        <el-button type="primary" @click="addDictVisible = false">
          保存
        </el-button>
      </span>
    </template>
  </el-dialog>
  <el-dialog v-model="addChildDictVisible" :title="`添加${dataDictForm.key_name}字典`">
    <el-form :model="dataDictForm">
      <el-form-item label="字典编号" >
        <el-input v-model="dataDictForm.dict_id" autocomplete="off" disabled/>
      </el-form-item>
      <el-form-item label="字典名称" >
        <el-input v-model="dataDictForm.key_name" autocomplete="off" clearable/>
      </el-form-item>
      <el-form-item label="字典值" >
        <el-input v-model="dataDictForm.key_value" autocomplete="off" clearable/>
      </el-form-item>
      <el-form-item label="字典url" >
        <el-input v-model="dataDictForm.key_url" autocomplete="off" clearable/>
      </el-form-item>
      <el-form-item label="字典其他" >
        <el-input v-model="dataDictForm.key_args" autocomplete="off" clearable/>
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="addChildDictVisible = false">取消</el-button>
        <el-button type="primary" @click="addChildDictVisible = false">
          保存
        </el-button>
      </span>
    </template>
  </el-dialog>
</template>


<style lang="scss" scoped>
.tb-table{
  display: flex;
  margin-bottom: 20px;
}
</style>
