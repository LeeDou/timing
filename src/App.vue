<template>
    <div>
        <count-down :start='start' @countDown ='start=false' @click.native='sendCode'></count-down>
    </div>
</template>
<script>
import CountDown from './components/CountDown.vue'
    export default {
        components: {
          CountDown 
        },
        data () {
            return {
                start : false
            }
        },
        methods : {
            sendCode (value) {
                //前面发送ajax请求成功之后调用this.start = true开始短信倒计时
                alert('发送ajax请求');
                this.start = true
            }
        }
    }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
