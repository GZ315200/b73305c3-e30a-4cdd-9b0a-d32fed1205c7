<template>
    <div class="login-wrap">
        <div class="ms-title">后台管理系统</div>
        <div class="ms-login">
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="0px" class="demo-ruleForm">
                <el-form-item prop="workId">
                    <el-input v-model="ruleForm.workId" placeholder="输入工号"></el-input>
                </el-form-item>
                <el-form-item prop="username">
                   <el-input v-model="ruleForm.username" placeholder="请输入账号"></el-input>
                </el-form-item>
                <el-form-item  prop="pass">
                    <el-input type="password" v-model="ruleForm.pass" placeholder="请输入密码" auto-complete="off"></el-input>
                    </el-form-item>
                <!-- <div class="msgCode-btn">
                    <el-button type="primary" @click="submitForm('')">发送验证码</el-button>
                </div>-->
                <div class="login-btn">
                    <el-button type="primary" @click="submitForm('ruleForm')" style="width:181px;">登录</el-button>
                    <el-checkbox v-model="checked" style="100px;">是否记住用户名和密码</el-checkbox>
                </div> 
                <p style="font-size:12px;line-height:30px;color:#999;">Tips : 用户名和密码随便填。</p>
            </el-form>
        </div>
    </div>
</template>

<script>
    export default {
        data: function(){
            return {
                ruleForm: {
                    workId:'',
                    username: '',
                    pass : ''
                },
                  checked: false,
                rules: {
                    workId: [
                        { required: true, message: '请输入工号', trigger: 'blur' }
                    ],
                    username: [
                        { required: true, message: '请输入账号', trigger: 'blur' }
                    ],
                    pass: [
                        { required: true, message: '输入密码', trigger: 'blur' }
                    ]
                }
            }
        },
        methods: {
            submitForm(formName) {
                const self = this;
                self.$refs[formName].validate((valid) => {
                    if (valid) {
                        localStorage.setItem('ms_username',self.ruleForm.username);
                        self.$router.push('/readme');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            }
        }
    }
</script>

<style scoped>
    .login-wrap{
        position: relative;
        width:100%;
        height:100%;
    }
    .ms-title{
        position: absolute;
        top:50%;
        width:100%;
        margin-top: -230px;
        text-align: center;
        font-size:30px;
        color: #fff;

    }
    .ms-login{
        position: absolute;
        left:50%;
        top:50%;
        width:350px;
        height:200px;
        margin:-150px 0 0 -190px;
        padding:40px;
        border-radius: 5px;
        background: #fff;
    }
    .login-btn{
        text-align: center;
    }
    .login-btn button{
        width:100%;
        height:36px;
    }
    .msgCode-btn{
        margin-top : -57.8px;
        float:right;
    }
</style>