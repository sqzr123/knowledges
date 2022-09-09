<template>
  <div>
    <el-row>
      <div
        class="grid-content bg-purple-dark login_bg"
        style="width: 270px; height: 304px"
      >
        <el-tabs v-model="activeName" @tab-click="handleClick">
          <el-tab-pane label="账号登录" name="first">
            <el-form
              :model="ruleForm"
              :rules="rules"
              ref="ruleForm"
              label-position="left"
              label-width="0px"
              class="login-form"
            >
              <el-form-item prop="username">
                <el-input
                  placeholder="账号"
                  v-model="ruleForm.username"
                  clearable
                >
                </el-input>
              </el-form-item>

              <el-form-item prop="password">
                <el-input
                  placeholder="密码"
                  v-model="ruleForm.password"
                  show-password
                  clearable
                >
                </el-input>
              </el-form-item>
              <el-row>
                <el-col :span="12"
                  ><div class="grid-content bg-purple">
                    <el-checkbox-group v-model="ruleForm.type">
                      <el-checkbox label="自动登录" name="type"></el-checkbox>
                    </el-checkbox-group></div
                ></el-col>
                <el-col :span="12"
                  ><div class="grid-content bg-purple-light ft_password">
                    忘记密码
                  </div></el-col
                >
              </el-row>

              <el-form-item style="width: 100%">
                <el-button
                  class="btn-login"
                  size="medium"
                  type="primary"
                  style="width: 100%"
                  @click="login('ruleForm')"
                >
                  <span>登 录</span>
                </el-button>
              </el-form-item>
              <p class="register">立即注册</p>
            </el-form>
          </el-tab-pane>
          <el-tab-pane label="扫码登录" name="second"></el-tab-pane>
        </el-tabs>
      </div>
    </el-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      activeName: "first",
      ruleForm: {
        username: "", //账号

        password: "", //密码
        type: "false",
      },
      rules: {
        //表单验证规则

        username: [
          { required: true, message: "请输入账号", trigger: "blur" },

          { min: 2, max: 6, message: "长度在 2 到 6 个字符", trigger: "blur" },
        ],

        password: [
          { required: true, message: "请输入密码", trigger: "blur" },

          {
            min: 6,

            max: 18,

            message: "长度在 6 到 18 个字符",

            trigger: "blur",
          },
        ],
      },
    };
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event);
    },
    login(formName) {
      //表单验证

      this.$refs[formName].validate((valid) => {
        if (valid) {
          let userInfo = {
            token: "sd",
          };

          this.$store

            .dispatch("LoginByUsername", userInfo)

            .then(() => {
              this.$router.push("/"); //页面跳转到首页
            })

            .catch(() => {});
        }
      });
    },
  },
};
</script>
<style scoped>
::v-deep .el-tabs .el-tabs__header .el-tabs__nav-wrap .el-tabs__nav-scroll {
  padding-left: 46px !important;
}
::v-deep
  .el-tabs
  .el-tabs__header
  .el-tabs__nav-wrap
  .el-tabs__nav-scroll
  #tab-first {
  color: #d5d5d6;
  font-size: 16px;
  font-family: Microsoft YaHei, Microsoft YaHei-Regular;
  font-weight: 400;
}
::v-deep
  .el-tabs
  .el-tabs__header
  .el-tabs__nav-wrap
  .el-tabs__nav-scroll
  .is-active {
  color: #fff !important;
}
::v-deep
  .el-tabs
  .el-tabs__header
  .el-tabs__nav-wrap
  .el-tabs__nav-scroll
  #tab-second,
#tab-first {
  color: #d5d5d6;
  font-size: 16px;
  font-family: Microsoft YaHei, Microsoft YaHei-Regular;
  font-weight: 400;
}
.login_bg {
  background: rgb(34, 34, 35, 0.7);
  opacity: 1;
}

::v-deep .el-form .el-form-item__content {
  width: 220px;
  height: 34px;
  background: #222223;
  border-radius: 3px;
  color: #d5d5d6;
  line-height: 0 !important;
}
::v-deep .el-form .el-form-item__content .el-input__inner {
  width: 220px;
  height: 34px;
  background: #222223;
  border-radius: 3px;
  color: #d5d5d6;
  border: 1px solid #222223 !important;
}

::v-deep .el-tabs .el-tabs__content {
  padding-left: 25px;
}
::v-deep .el-tabs .el-form-item__content .el-button {
  /* margin-top: 20px; */
  margin-bottom: 20px;
  background-color: #ffa031 !important;
  border: #ffa031 !important;
}
::v-deep .grid-content .el-checkbox-group {
  position: relative;
  left: -20px;
  margin-bottom: 20px;
}
::v-deep .grid-content .el-checkbox-group .el-checkbox__label {
  font-size: 12px;
  font-family: Microsoft YaHei, Microsoft YaHei-Regular;
  font-weight: 400;
  color: #f5f5f5;
}
.register {
  font-size: 12px;
  font-family: Microsoft YaHei, Microsoft YaHei-Regular;
  font-weight: 400;
  cursor: pointer;
  color: #f5f5f5;
  letter-spacing: 0.36px;
  width: 220px;
}
.ft_password {
  cursor: pointer;
  font-size: 12px;
  font-family: Microsoft YaHei, Microsoft YaHei-Regular;
  font-weight: 400;
  color: #f5f5f5;
  text-align: center;
}
::v-deep .el-tabs__active-bar {
  background-color: #ffa031;
}
::v-deep .el-tabs__nav-wrap::after {
  content: "";
  position: absolute;
  left: 25px;
  bottom: 0;
  width: 100%;
  height: 2px;
  background-color: #e4e7ed;
  z-index: 1;
  width: 220px;
}
</style>