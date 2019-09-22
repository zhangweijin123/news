<template>
  <!-- @input是输入框每次输入的时候都会触发 -->
  <input
   class="input"
   :placeholder="placeholder"
   :value="value"
   @input="handleInput"
   />
</template>

<script>
export default {
    props:[
        "placeholder",
        "value",
        "name",

        "rule",
    ],

    methods:{
        //每次输入框输入值的时候都会触发
        handleInput(event){
            this.$emit("input",event.target.value)
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
</style>