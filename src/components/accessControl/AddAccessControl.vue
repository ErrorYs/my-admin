<template>
  <el-dialog class="big-dialog AddAccessControl" title="添加权限" :visible.sync="showFlag">
    <el-form :model="formData" :rules="rules" ref="formData" label-width="80px" class="demo-formData">
      <el-form-item label="权限名称" prop="name">
        <el-input v-model="formData.name"></el-input>
      </el-form-item>
      <el-form-item label="描述" prop="desc">
        <el-input v-model="formData.desc"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="submitForm('formData')">立即创建</el-button>
        <el-button @click="resetForm('formData')">重置</el-button>
      </el-form-item>
    </el-form>
  </el-dialog>
</template>

<script>
export default {
  name: 'AddAccessControl',
  data () {
    return {
      showFlag: false,
      formData: {
        name: '',
        desc: ''
      },
      rules: {
        name: [
          { required: true, message: '请输入权限名', trigger: 'blur' }
        ],
        desc: [
          { required: true, message: '请输入描述', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    submitForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert('submit!')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<style scoped lang="scss">
  .AddAccessControl {

  }
</style>
