<template>
    <div class="login-container">
      <title>Test Login page</title>
      <el-row class="login-row">
        <!-- 左侧栏，放置图标 -->
        <el-col :span="12" class="login-left">
            
                <img :src="url" alt="Deam image" width=200>
        
        </el-col>
        
        <!-- 右侧栏，放置帐号和密码输入框 -->
        <el-col :span="12" class="login-right">
          <el-form ref="ruleFormRef" :model="form" class="login-form" :rules="rules" >  <!-- 定義同名var-->

            <el-form-item label="Will Test Page" prop="userName"></el-form-item>

            <el-form-item label="帐号" prop="userName">
              <el-input v-model="form.userName" placeholder="请输入帐号"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="passWord">
              <el-input v-model="form.passWord" type="passWord" placeholder="请输入密码" @keyup.enter="onSubmit(rulesFormRef)"/>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit(rulesFormRef)">登录</el-button>
            </el-form-item>
          </el-form>
        </el-col>
      </el-row>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { ElMessage, FormInstance, FormRules } from 'element-plus';
  import { reactive, ref } from 'vue';
  


  const url = ref('/images/Logo.png'); // in public
 
  const form = reactive({
    userName: '',
    passWord: '',
  });
  
  const rulesFormRef = ref<FormInstance>();
  const rules = reactive<FormRules>(
    {
      userName: [
        { required: true, message: '请输入帐号', trigger: 'blur' },
      ],
      passWord: [
        { required: true, message: '请输入密码', trigger: 'blur', type: 'number' },
      ],
    },
  );
  const onSubmit =async (rulesFormRef: FormInstance | undefined) => {
    if (!rulesFormRef) return;
    await rulesFormRef.validate(async (valid, fields) => {
        if (valid) {
          ElMessage.success('登录成功');
        } else {
        let errors: string = "";
        fields?.userName?.forEach(element => {
            errors += element.message + ";";
        });
        fields?.passWord?.forEach(element => {
            errors += element.message + ";";
        });
        ElMessage.error(errors);
        }
    });  
    console.log(form);
  }


    


  
  
  </script>
  
  <style lang="scss" scoped>
  /* 自定义样式 */

  </style>
  