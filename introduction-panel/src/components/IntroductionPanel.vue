<template>
    <div class="introduction introduction-panel">
        <div class="introduction introduction-wrapper" v-bind:class="{'active':introduction_active}">
            <div class="introduction rope"></div>
            <div class="introduction introduction-bar">
                <div v-for="(introduction,field) in introductions" v-bind:key="field">
                    <p>{{field}}</p>
                    <p>{{introduction}}</p><br><br>
                </div>
            </div>
        </div>
        <div class="introduction introduction-trigger" v-bind:class="{'active':introduction_active}">
            <div class="introduction trigger-rope"></div>
            <div class="introduction trigger-point" @click="changeActiveStatus()" v-bind:class="{'active':introduction_active}">
                <div class="arrow arrow-down"></div>
                <div class="arrow arrow-down"></div>
                <div class="arrow arrow-down"></div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "IntroductionPanel",
        data() {
            return{
                introduction_active: false,
                introductions: {
                    '用户名：': '6-20位，可包含英文字母、阿拉伯数字和下划线("_")以及横线("-")，其中，英文字母大小写不敏感。}',
                    '邮箱：': '邮箱用于接收注册验证码和登录，后期通知也通过该邮箱下发，请输入有效的邮箱地址。',
                    '验证码：': '6位数字。验证码用于校验输入的邮箱是否属于您本人，验证码有效期为5分钟。',
                    '密码：': '6-20位字符。密码用于账号登录，请保管好您的密码，不要轻易透露给他人。密码不能包含空格以及，此外无特殊要求。'
                }
            }
        },
        methods: {
            changeActiveStatus(){
                this.introduction_active = !this.introduction_active;
            }
        }
    }
</script>

<style scoped>

    /*所有元素的动画效果*/
    .introduction{
        transition: 0.3s cubic-bezier(.37,1.44,.57,.77);
    }

    /*左侧部分*/
    .introduction.introduction-wrapper{
        width: 100%;
        position: absolute;
        top: -1000px;/*左侧部分一开始应该在浏览器上分，在视野之外*/
        text-align: center;
    }

    /*左侧变换后的位置*/
    .introduction.introduction-wrapper.active{
        top: -5px;/*-5是为了遮住绳子的div的上面部分*/
    }

    /*牵引绳*/
    .introduction.rope{
        width: 200px;
        height: 100px;
        border-left: 5px rgba(0,129,198,.8) solid;
        border-right: 5px rgba(0,129,198,.8) solid;
        box-shadow: 0px 0px 5px 0px rgba(13,148,225,.8), 0px 0px 5px 0px rgba(13,148,225,.8) inset;
        margin: 0 auto;
    }

    /*内容面板*/
    .introduction.introduction-bar{
        width: 500px;
        height: 600px;
        margin: 0 auto;
        text-align: left;
        color: rgba(13,148,225,.9);/*内容颜色，蓝色加透明*/
        padding: 40px 60px;
        top: -5px;
        position: relative;
        border-radius: 5px;/*圆角*/
        background-color: rgba(254, 253, 255, 0.9);/*背景色，白色加透明*/
        box-shadow: 0 7px 25px rgba(0, 0, 0, .3);/*阴影*/
    }

    /*开关整体*/
    .introduction.introduction-trigger{
        top: 0px;/*开关一开始的高度*/
        left: 80%;
        position: absolute;
        text-align: center;
    }

    /*开关整体变换后的高度*/
    .introduction.introduction-trigger.active{
        top: -150px;/*往浏览器上方走，相当于缩短。也可以设置仅开关上方的绳子变短*/
    }

    /*开关的绳子*/
    .introduction.trigger-rope{
        position: relative;
        width: 5px;
        height: 300px;
        margin: 0 auto;
        background-color: rgba(0,129,198,.8);
        box-shadow: 0px 0px 5px 0px rgba(13,148,225,.8);
    }

    /*开关下方绳结*/
    .introduction.trigger-point{
        margin: 0 auto;
        position: relative;
        width: 25px;
        height: 60px;
        background-color: rgba(0,129,198,.9);
        box-shadow: 0px 0px 5px 0px rgba(13,148,225,.8);
        border-radius: 5px;
        text-align: center;
        cursor: pointer;
    }

    /*未激活的绳结需要设置底部padding，以抵消箭头旋转后产生的上下偏移*/
    .introduction.trigger-point:not(.active){
        padding-bottom: 8px;
    }

    /*绳结下方的提示，未激活时显示*/
    .introduction.trigger-point:not(.active):before{
        content: '点击查看帮助';
        color: rgba(13,148,225,.8);
        width: 100px;
        position: absolute;
        left: 50%;
        top:100%;
        transform: translateX(-50%);
    }

    /*绳结激活后，绳结上的箭头旋转*/
    .introduction.trigger-point.active > .arrow-down{
        transform: rotate(225deg);
    }

    /*div的两条边邻边*/
    .arrow {
        border: solid #ffffff;
        border-width: 0 3px 3px 0;
        display: inline-block;
        padding: 5px;
        margin: 0 auto;
    }

    /*div旋转形成箭头*/
    .arrow-down {
        transform: rotate(45deg);
        -webkit-transform: rotate(45deg);
    }
</style>
