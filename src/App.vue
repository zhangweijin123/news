<template>
  <div>
      <!-- 组件占位符 -->
      <router-view></router-view>
  </div>
</template>

<script>
export default {
    data(){
        return {
            
        }
    }
} 
</script>

<style>
*{
    margin:0;
    padding:0
}
a{
    color:inherit;
}
a:hover{
    text-decoration: underline;
}
ul,li,ol{
    list-style: none;
}
i,em{
    font-style: none;
}
</style>