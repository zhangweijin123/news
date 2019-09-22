<template>
  <!-- @input是输入框每次输入的时候都会触发 -->
  <input
   class="input"
   :class="{
       success: status === 'success',
       error: status === 'error'
   }"
   :placeholder="placeholder"
   :value="value"
   @input="handleInput"
   @change="handleChange"
   />
</template>

<script>
export default {
    data(){
        return{
            status:''
        }
    },
    //rule传递过来的正则表达式
    props:[
        "placeholder",
        "value",
        "name",

        "rule",
        "err_message"
    ],

    methods:{
        //每次输入框输入值的时候都会触发
        handleInput(event){
            // this.$emit("input",event.target.value)
            const {value} = event.target;

            //触发父组件的input事件 返回输入框的值
            this.$emit("input",value);

            //如果符合正则就位success 反之是error
            if(this.rule){
                if(this.rule.test(value)){
                    this.status === "success";
                } else {
                    this.status === "error";
                }
            }
        },

        //输入框失去焦点的时候触发
        handleChange(){
            if(this.err_message){
                alert(this.err_message);
            }
        }
    }
}
</script>

<style scoped lang="less">
    .input{
        width: 100%;
        height: 38 /360 *100vw;
        padding: 20px;
        box-sizing: border-box;
        background: #fff;
        border:none;
        border-bottom: 2px #666 solid;
        outline: none;
    }

    .success{
        border-color: blue;
    }

    .error{
        border-color: red;
    }
</style>