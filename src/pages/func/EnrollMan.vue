<template>
  <h1 style="margin-bottom: 20px; padding: 10px; text-align: center;">报名管理页面</h1>
  <a-row>
    <a-col :span="2" :offset="1">选择部门</a-col>
    <a-col :span="4">
      <a-select v-model:value="selectedDept" style="width: 100%">
        <a-select-option value=""></a-select-option>
        <a-select-option v-for="(item, index) in deptList" :key="index" :value="item">{{item}}</a-select-option>
      </a-select>
    </a-col>
    <a-col>
      <a-button type="primary" @click="queryEnroll">查询</a-button>
    </a-col>
  </a-row>
  <a-table :dataSource="queryData" :columns="columns" :scroll="{x: 800 ,y: 400}" style="margin-top: 10px">
    <template #bodyCell="{ column }">
      <template v-if="column.key === 'operation'">
        <a>查看详情</a>
      </template>
    </template>
  </a-table>
    
</template>

<script>
export default {
  data() {
    return {
      queryData: [],
      enrollData: [],
      selectedDept: '',
      columns: [
        { title: '学号', dataIndex: 'stu_id', key: 'stu_id', fixed: 'left'},
        { title: '姓名', dataIndex: 'name', key: 'name', fixed: 'left'},
        { title: '性别', dataIndex: 'sex', key: 'sex' },
        { title: '第一志愿', dataIndex: 'firstChoice', key: 'firstChoice' },
        { title: '第二志愿', dataIndex: 'secondChoice', key: 'secondChoice' },
        { title: '学院', dataIndex: 'dept', key: 'dept'},
        { title: '手机', dataIndex: 'tel', key: 'tel'},
        { title: '邮箱', dataIndex: 'email', key: 'email'},
        { title: '特长', dataIndex: 'speciality', key: 'speciality'},
        { title: '学生工作经历', dataIndex: 'info', key: 'info' },
        { title: '操作', key: 'operation', width: 100, fixed: 'right'}
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
      
    }
  },
  mounted() {
    this.enrollData = [        
      {key: '1', stu_id: '123', name: '测试学生1', sex: '男', firstChoice: this.deptList[0]},
      {key: '2', stu_id: '123', name: '测试学生2', sex: '男', firstChoice: this.deptList[1]},
      {key: '3', stu_id: '123', name: '测试学生3', sex: '男', firstChoice: this.deptList[1]},
      {key: '4', stu_id: '123', name: '测试学生4', sex: '男', firstChoice: this.deptList[0], secondChoice: this.deptList[1]},
      {key: '5', stu_id: '123', name: '测试学生5', sex: '男', firstChoice: this.deptList[2]},
      {key: '6', stu_id: '123', name: '测试学生6', sex: '男', firstChoice: this.deptList[2]},
      {key: '7', stu_id: '123', name: '测试学生7', sex: '男', firstChoice: this.deptList[3]},
      {key: '8', stu_id: '123', name: '测试学生8', sex: '男', firstChoice: this.deptList[4]},
      {key: '9', stu_id: '123', name: '测试学生9', sex: '男', firstChoice: this.deptList[4]},
      {key: '10', stu_id: '123', name: '测试学生10', sex: '男', firstChoice: this.deptList[4]},
      ]
    this.queryData = this.enrollData
  },
}
</script>

<style scoped>
</style>