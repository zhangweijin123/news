<template>
  <div class="colorRed">
      这是第一个单文件组件，{{message}}, 132465456

      <router-link to="/login">登录页</router-link>
      
      <router-view></router-view>
  </div>
</template>

<script>
export default {
    data(){
        return {
            message: "hello vue"
        }
    }
} 
</script>

<style>
    .colorRed{
        color:red;
    }
</style>