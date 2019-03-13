<template>
  <div>
     <x-header style="background-color:#409EFF;" title="use prop:title">登录</x-header>
    <group>
      <x-input title="手机号码" placeholder="请输入您的手机号码" mask="999 9999 9999" :max="13" is-type="china-mobile"></x-input>
      <x-input title="身份证号" placeholder="请输入您的身份证号" type="password" :max="20" :min="15"></x-input>
      <x-input title="密码" v-model="password" placeholder="请输入密码" type="password" :min="15"></x-input>
      <x-button type="primary" @click.native="back">登录</x-button>
    </group>
  </div>
</template>

<script>
import { XInput, XHeader, XButton, Group, AlertModule } from 'vux'

export default {
  components: {
    XButton,
    XInput,
    XHeader,
    Group,
    AlertModule
  },
  methods: {
    back () {
      if (this.password === '123') {
        this.$router.push('/')
      } else {
        AlertModule.show({
          title: '密码错误'
        })
      }
    }
  },
  data () {
    return {
      password: '',
      msg: 'Hello World!'
    }
  }
}
</script>

<style>
.vux-demo {
  text-align: center;
}
.button.weui-btn, input.weui-btn{
  width:80%;
  background-color:#409EFF;
}
.logo {
  width: 100px;
  height: 100px
}
</style>
