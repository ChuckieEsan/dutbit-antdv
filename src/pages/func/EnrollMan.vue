<template>
  <h1 style="margin-bottom: 20px; padding: 10px; text-align: center;">报名管理页面</h1>
  <a-row type="flex" align="middle">
    <a-col :span="3" :offset="1" style="text-align: right; padding-right: 10px">选择部门</a-col>
    <a-col :span="4">
      <a-select v-model:value="selectedDept" style="width: 100%">
        <a-select-option value="">全部</a-select-option>
        <a-select-option v-for="(item, index) in deptList" :key="index" :value="item">{{item}}</a-select-option>
      </a-select>
    </a-col>
    <a-col>
      <a-button type="primary" @click="queryEnroll">查询</a-button>
    </a-col>
  </a-row>
  <a-table :dataSource="queryData" :columns="columns" :scroll="{x: '120%', y: 400}" style="margin-top: 10px">
    <template #bodyCell="{ column, record }">
      <template v-if="column.key === 'operation'">
        <a @click="handleInfo(record.key)">查看详情</a>
      </template>
    </template>
  </a-table>
  <a-modal v-model:visible="infoModalVisible" title="资料详情">
    <template #footer>
      <a-button key="ok" type="primary"  @click="infoModalVisible = false">确定</a-button>
    </template>
    <a-descriptions title="报名信息" bordered :column="4">
      <a-descriptions-item label="姓名" :span="2">{{ queryData[recordIndex].name }}</a-descriptions-item>
      <a-descriptions-item label="学号" :span="2">{{ queryData[recordIndex].stu_id }}</a-descriptions-item>
      <a-descriptions-item label="性别" :span="4">{{ queryData[recordIndex].sex }}</a-descriptions-item>
      <a-descriptions-item label="第一志愿" :span="4">{{ queryData[recordIndex].firstChoice }}</a-descriptions-item>
      <a-descriptions-item label="第二志愿" :span="4">{{ queryData[recordIndex].secondChoice }}</a-descriptions-item>
      <a-descriptions-item label="学院" :span="4">{{ queryData[recordIndex].dept }}</a-descriptions-item>
      <a-descriptions-item label="手机" :span="4">{{ queryData[recordIndex].tel }}</a-descriptions-item>
      <a-descriptions-item label="邮箱" :span="4">{{ queryData[recordIndex].email }}</a-descriptions-item>
      <a-descriptions-item label="特长" :span="4">{{ queryData[recordIndex].speciality }}</a-descriptions-item>
      <a-descriptions-item label="学生工作经历" :span="4">{{ queryData[recordIndex].info }}</a-descriptions-item>
    </a-descriptions>
  </a-modal>
    
</template>

<script>
import { defineComponent, ref } from 'vue';
export default {
  data() {
    return {
      queryData: [],
      enrollData: [],
      selectedDept: '',
      infoModalVisible: false,
      recordIndex: 0,
      columns: [
        { title: '学号', dataIndex: 'stu_id', key: 'stu_id', fixed: 'left', width: 120},
        { title: '姓名', dataIndex: 'name', key: 'name', fixed: 'left', width: 100},
        { title: '性别', dataIndex: 'sex', key: 'sex', width: 60 },
        { title: '第一志愿', dataIndex: 'firstChoice', key: 'firstChoice', width: 150 },
        { title: '第二志愿', dataIndex: 'secondChoice', key: 'secondChoice', width: 150 },
        { title: '学院', dataIndex: 'dept', key: 'dept', width: 150 },
        { title: '手机', dataIndex: 'tel', key: 'tel', width: 120 },
        { title: '邮箱', dataIndex: 'email', key: 'email', width: 200 },
        { title: '特长', dataIndex: 'speciality', key: 'speciality', width: 200 },
        { title: '学生工作经历', dataIndex: 'info', key: 'info', width: 200 },
        { title: '操作', key: 'operation', fixed: 'right',  width: 120 }
      ]
    }
  },
  components: {},
  computed: {},
  inject: ['deptList'],
  provide() {
    return {}
  },
  methods: {
    queryEnroll() {
      console.log(this.selectedDept)
      if(this.selectedDept) {
        this.queryData = this.enrollData.filter((p) => {
        if(p.firstChoice === this.selectedDept || p.secondChoice === this.selectedDept)
          return p
        })
      } else {
        this.queryData = this.enrollData
      }
    },
    handleInfo(key) {
      this.infoModalVisible = !this.infoModalVisible
      this.queryData.forEach((p, index) => {
        if(p.key === key) {
          this.recordIndex = index 
        }
      })
    }
  },
  mounted() {
    this.enrollData = [        
      {key: 'testkey', stu_id: '123', name: '测试学生1', sex: '男', firstChoice: this.deptList[0]},
      {key: '2', stu_id: '123', name: '测试学生2', sex: '男', firstChoice: this.deptList[1]},
      {key: '3', stu_id: '123', name: '测试学生3', sex: '男', firstChoice: this.deptList[1]},
      {key: '4', stu_id: '123', name: '测试学生4', sex: '男', firstChoice: this.deptList[0], secondChoice: this.deptList[1]},
      {key: '5', stu_id: '123', name: '测试学生5', sex: '男', firstChoice: this.deptList[2]},
      {key: '6', stu_id: '123', name: '测试学生6', sex: '男', firstChoice: this.deptList[2]},
      {key: '7', stu_id: '123', name: '测试学生7', sex: '男', firstChoice: this.deptList[3]},
      {key: '8', stu_id: '123', name: '测试学生8', sex: '男', firstChoice: this.deptList[4]},
      {key: '9', stu_id: '123', name: '测试学生9', sex: '男', firstChoice: this.deptList[4]},
      {
        key: '10', 
        stu_id: '20201111109', 
        name: '刘晨昱', 
        sex: '男', 
        firstChoice: this.deptList[4], 
        dept:'经济管理学院',
        tel: '15036562977',
        email: 'liuchenyu222@163.com',
        speciality: '不知道写什么',
        info: '融媒体中心技术部部长'
        },
      ]
    this.queryData = this.enrollData
  },
}
</script>

<style scoped>
</style>