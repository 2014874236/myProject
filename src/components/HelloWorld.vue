<template>
  <div class="login">
    <img src="../assets/img/login1.png" alt="" class="logIcon">
    <div class="login-container">
      <el-form>   <!-- :model="loginForm" :rules="loginRules" ref="loginForm" class="card-box login-form" -->
          <h1 class="title">茶叶商城</h1>
          <el-form-item prop="userName" class="item userItem">
              <span class="svg-container">
                <i class="fa fa-user-o" aria-hidden="true"></i>
              </span>
              <el-input name="userName" type="text"   placeholder="用户名" class="input-content"></el-input> <!-- v-model="loginForm.userName"   v-model="loginForm.password"-->
          </el-form-item>
          <el-form-item prop="password" class="item">
              <span class="svg-container">
                <i class="fa fa-lock" aria-hidden="true"></i>
              </span>
              <el-input name="password" type="password"  placeholder="密码" class="input-content"></el-input>   <!--  @keyup.enter.native="handleLogin" -->
          </el-form-item>
          <el-form-item>
            测试账号：1111/vuex  密码：123456
          </el-form-item>
          <el-form-item>
              <el-button type="primary"  >  <!-- @click="handleLogin" -->
                  登录
              </el-button>
              <el-button type="primary">
                  <!-- <router-link to="/register">注册</router-link> -->
              </el-button>
          </el-form-item>
      </el-form>
    </div>
    <!-- <router-view></router-view> -->
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data(){
        var validateUserName=(rule, value, callback) =>{
          console.log("aaaa");
          if(!value){
            callback(new Error("请输入用户名"));
          }
          else{
            if(value != "1111" && value != "vuex"){
              callback(new Error("用户名不存在"));
            }   
            else{
              callback();
            }
            // this.$http.get('../../static/login.json').then(function(response){
              // var flag=0;
              // for(let i=0;i<this.username.length;i++){
              //  if(value === this.username[i].username){
              //    flag=1;
              //    this.loginForm.psw=this.username[i].password;
              //    break;
              //  }
              // }
              // if(flag !=1){
              //  callback(new Error("用户名不存在"));
              // }
            // });
          }
          

        };
        var validatePass = (rule, value, callback) => {
              if (value === '') {
                  callback(new Error('请输入密码'));
              } 
              else if(value.length<6){
                  callback(new Error('密码不能少于6位'));
              }
              else if(value != "123456")
              // else if(value != this.loginForm.psw){
                callback(new Error('密码错误'));
              // }
              else{
                callback();
              }
          };
        return{
          // loginForm:store.state.userInfo,
          loading:false,
          loginRules:{
            userName:[
              {validator: validateUserName, trigger: 'blur' }
            ],
            password:[
              {validator: validatePass, trigger: 'blur' }
            ]
          }
        };
        
      },
      methods:{
        // handleLogin:function(){
        //    this.$refs.loginForm.validate((valid) => {
        //           if (valid) {
        //             this.$router.push({ path: 'home/hello',component:Hello});
        //         } else {
        //             console.log('error submit!!');
        //             return false;
        //         }
        //       });
        // } 
      },
      mounted:function(){
          // console.log("stor内容" ,store.state.userInfo);
      }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss" scoped>
  @import '../assets/stylesheets/universal.scss';
  
  /*@import 'style/universal.scss';*/
  .login{
    overflow: hidden;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    .logIcon{
      float: left;
    }
    .login-container{
      float: left;
      .title{
        font-size: 40px;
      }
    }
  }
</style>
