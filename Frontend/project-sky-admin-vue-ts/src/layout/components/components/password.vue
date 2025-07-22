<template>
  <el-dialog
    title="Change Password"
    :visible.sync="dialogFormVisible"
    width="568px"
    class="pwdCon"
    @close="handlePwdClose()"
  >
    <el-form :model="form" label-width="160px" :rules="rules" ref="form">
      <el-form-item label="Old Password:" prop="oldPassword">
        <el-input
          v-model="form.oldPassword"
          type="password"
          placeholder="Please Enter"
        ></el-input>
      </el-form-item>
      <el-form-item label="New Password:" prop="newPassword">
        <el-input
          v-model="form.newPassword"
          type="password"
          placeholder="6 - 20 characters password, numbers or letters, case sensitive"
        ></el-input>
      </el-form-item>
      <el-form-item label="Confirm Password:" prop="affirmPassword">
        <el-input
          v-model="form.affirmPassword"
          type="password"
          placeholder="Please Enter"
        ></el-input>
      </el-form-item>
    </el-form>
    <div slot="footer" class="dialog-footer">
      <el-button @click="handlePwdClose()">取 消</el-button>
      <el-button type="primary" @click="handleSave()">保 存</el-button>
    </div>
  </el-dialog>
</template>
<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import { Form as ElForm, Input } from 'element-ui'
// 接口
import { editPassword } from '@/api/users'
@Component({
  name: 'Password',
})
export default class extends Vue {
  @Prop() private dialogFormVisible!: any
  private validatePwd = (rule: any, value: any, callback: Function) => {
    const reg = /^[0-9A-Za-z]{6,20}$/
    if (!value) {
      callback(new Error('Please Enter'))
    } else if (!reg.test(value)) {
      callback(new Error('6 - 20 characters password, numbers or letters, case sensitive'))
    } else {
      callback()
    }
  }
  private validatePass2 = (rule, value, callback) => {
    if (!value) {
      callback(new Error('Please Enter Your Password Again'))
    } else if (value !== this.form.newPassword) {
      callback(new Error('The passwords do not match. Please re-enter your password.'))
    } else {
      callback()
    }
  }
  rules = {
    oldPassword: [{ validator: this.validatePwd, trigger: 'blur' }],
    newPassword: [{ validator: this.validatePwd, trigger: 'blur' }],
    affirmPassword: [{ validator: this.validatePass2, trigger: 'blur' }],
  }
  private form = {} as any
  private affirmPassword = ''
  handleSave() {
    ;(this.$refs.form as ElForm).validate(async (valid: boolean) => {
      if (valid) {
        const parnt = {
          oldPassword: this.form.oldPassword,
          newPassword: this.form.newPassword,
        }
        await editPassword(parnt)
        this.$emit('handleclose')
        ;(this.$refs.form as ElForm).resetFields()
      } else {
        return false
      }
    })
  }
  handlePwdClose() {
    ;(this.$refs.form as ElForm).resetFields()
    this.$emit('handleclose')
  }
}
</script>
<style lang="scss">
.navbar {
  .pwdCon {
    .el-dialog__body {
      // chinese char setting
      // padding-top: 60px;
      // padding: 60px 100px 0;
      padding: 40px 80px 0;
    }
    .el-input__inner {
      // padding: 0 12px;
      padding: 0 12px;
      height: 36px;
      font-size: 14px;
    }
    .el-form-item {
      // margin-bottom: 26px;
      margin-bottom: 24px;
    }
    .el-form-item__label {
      // text-align: left;
      text-align: left;
      white-space: nowrap; // prevent line break
      font-size: 14px;
      line-height: 1.4;
      width: 160px !important; // Wider label width to fit English
      padding-right: 12px;
      white-space: normal; // allows wrapping if necessary
    }
    .el-dialog__footer {
      // padding-top: 14px;
      padding-top: 20px;
      text-align: right;

      .el-button {
        min-width: 80px;
      }
    }
  }
}
</style>