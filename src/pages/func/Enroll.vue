<template>
  <div style="container">
    <h1 style="margin-bottom: 20px; padding: 10px; text-align: center;">报名页面</h1>
    <a-form :model="signupForm" name="signup" :label-col="{span: 8}" :wrapper-col="{span: 8}" autocomplete="off">
      <a-form-item label="学号" name="num">
        <a-input v-model:value="signupForm.num" />
      </a-form-item>
      <a-form-item label="姓名" name="name">
        <a-input v-model:value="signupForm.name" />
      </a-form-item>
      <a-form-item label="性别" name="sex">
        <a-radio-group v-model:value="signupForm.sex">
          <a-radio value="male">男</a-radio>
          <a-radio value="female">女</a-radio>
        </a-radio-group>
      </a-form-item>
      <a-form-item label="学院" name="dept">
        <a-select v-model:value="signupForm.dept">
          <a-select-option value="电子信息与电气工程学部">电子信息与电气工程学部</a-select-option>
          <a-select-option value="建设工程学部">建设工程学部</a-select-option>
          <a-select-option value="人文与社会科学学部">人文与社会科学学部</a-select-option>
          <a-select-option value="运载工程与力学学部">运载工程与力学学部</a-select-option>
          <a-select-option value="材料科学与工程学院">材料科学与工程学院</a-select-option>
          <a-select-option value="光电工程与仪器科学学院">光电工程与仪器科学学院</a-select-option>
          <a-select-option value="化工学院">化工学院</a-select-option>
          <a-select-option value="环境学院">环境学院</a-select-option>
          <a-select-option value="机械工程学院">机械工程学院</a-select-option>
          <a-select-option value="建筑与艺术学院">建筑与艺术学院</a-select-option>
          <a-select-option value="经济管理学院">经济管理学院</a-select-option>
          <a-select-option value="能源与动力学院">能源与动力学院</a-select-option>
          <a-select-option value="生物工程学院">生物工程学院</a-select-option>
          <a-select-option value="数学科学学院">数学科学学院</a-select-option>
          <a-select-option value="外国语学院">外国语学院</a-select-option>
          <a-select-option value="物理学院">物理学院</a-select-option>
          <a-select-option value="张大煜学院">张大煜学院</a-select-option>
          <a-select-option value="大连理工大学白俄罗斯国立大学联合学院">
              大连理工大学白俄罗斯国立大学联合学院
          </a-select-option>
        </a-select>
      </a-form-item>
      <a-form-item label="手机" name="tel">
        <a-input v-model:value="signupForm.tel" />
      </a-form-item>
      <a-form-item label="邮箱" name="email">
        <a-input v-model:value="signupForm.email" />
      </a-form-item>
      <a-form-item label="特长" name="speciality">
        <a-input v-model:value="signupForm.speciality" />
      </a-form-item>
      <a-form-item label="学生工作经历" name="info">
        <a-textarea v-model:value="signupForm.info" />
      </a-form-item>
      <a-form-item :wrapperCol="{offset: 8, span: 8}">
        <a-button type="primary" html-type="submit">提交</a-button>
      </a-form-item>
    </a-form>
  </div>
</template>

<script>
import { defineComponent, reactive } from 'vue'
export default {
  components: {},
  data() {
    return {
      signupForm: {
        num: '',
        name: '',
        sex: '',
        dept: '',
        tel: '',
        email: '',
        speciality: '',
        info: '',
      },
    }
  },
  computed: {},
  inject: [],
  provide() {
    return {}
  },
  methods: {},
  mounted() {
    
  },
}
</script>

<style scoped>

</style>