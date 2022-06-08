<template>
  <div class="hello">
    <div class="headerTitle">Login</div>
    <el-form :model="form" label-width="80px">
      <el-form-item label="用户名： ">
        <el-input size="small" v-model="form.name" placeholder="请输入用户名"></el-input>
      </el-form-item>
      <el-form-item label="密码： ">
        <el-input size="small" type="password" v-model="form.passdword" placeholder="请输入密码"></el-input>
      </el-form-item>
    </el-form>
    <div>
      <el-button size="small" type="primary" @click="onSubmit">登 陆</el-button>
      <el-button size="small" >取 消</el-button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "Login",
      LoginTime:"",
      form: {
          name: '',
          passdword:''
        }
    };
  },
  methods: {
      onSubmit() {
        if(this.form.name&&this.form.passdword){
          localStorage.setItem("namekey",this.form.name)
          this.GetTime()
          this.$router.push({
            path: '/index'
          })
        }else {
          this.$alert('请输入用户名或密码', '提示', {
            confirmButtonText: '确定'
          })
        }
      },
      GetTime() {
          var date = new Date(); //创建时间对象
          var year = date.getFullYear(); //获取年   
          var month = date.getMonth() + 1;//获取月   
          var day = date.getDay(); //获取当日
          var Hours = date.getHours();       //获取当前小时数(0-23)
          var Minutes = date.getMinutes();     //获取当前分钟数(0-59)
          var Seconds = date.getSeconds();     //获取当前秒数(0-59)
          this.LoginTime = year + "年" + month + "月" + day + "日"+ " " + " " + Hours + ":" + Minutes;
          window.sessionStorage.setItem("Times",this.LoginTime)
          
      }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.hello {
  border: 1px solid #999999;
  width: 450px;
  height: 200px;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  border-radius: 12px;
  cursor: pointer;
  margin: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .headerTitle {
    height: 40px;
    line-height: 40px;
    font-size: 32px;
    position: absolute;
    top: -80px;

  }
}
</style>
