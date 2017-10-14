<template>
     <div>
        <button>{{time | change}}</button>
     </div>
</template>

<script>
let flag = false
    export default {
        data () {
            return {
                time : '获取验证码',
            }
        },
        props : {
            start : {
                type : Boolean
            }
        },
        watch : {
            start (value,oldvalue) {
                if(value == true){
                    this.countDown()
                }
            }
        },
        methods: {
            countDown () {
                this.time = 60;
                let time = setInterval(()=>{
                    this.time --
                    if(this.time == 0){
                        this.$emit('countDown')
                        this.time = '获取验证码'
                        flag = true
                        clearInterval(time)
                    }
                },1000)
            }
        },
        filters : {
            change (value) {
               if(!value) return ""
               if(!isNaN(value)){
                   if(flag == true){
                       return `重新发送${value}S`
                   }
                   return value+'S后可重新发送验证码'
               }else{
                   return value
               }
            }
        }

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
