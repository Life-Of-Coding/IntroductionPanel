<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <IntroductionPanel>
      <template v-slot:title>
          <div align="center"><h1>注册指引</h1></div>
      </template>
      <template v-slot:content>
          <div v-for="(introduction,field) in introductions" v-bind:key="field">
              <p>{{field}}</p>
              <p>{{introduction}}</p><br><br>
          </div>
      </template>
  </IntroductionPanel>
</template>

<script>
import IntroductionPanel from "./components/IntroductionPanel"

export default {
  name: 'App',
  components: {
    IntroductionPanel
  },
  data() {
      return {
          introductions: {
              '用户名：': '6-20位，可包含英文字母、阿拉伯数字和下划线("_")以及横线("-")，其中，英文字母大小写不敏感。}',
              '邮箱：': '邮箱用于接收注册验证码和登录，后期通知也通过该邮箱下发，请输入有效的邮箱地址。',
              '验证码：': '6位数字。验证码用于校验输入的邮箱是否属于您本人，验证码有效期为5分钟。',
              '密码：': '6-20位字符。密码用于账号登录，请保管好您的密码，不要轻易透露给他人。密码不能包含空格以及，此外无特殊要求。'
          }
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
