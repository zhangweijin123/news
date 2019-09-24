<template>
  <div>
    <div class="personal">
      <!-- <img src="../../static/头像.jpg" alt /> -->
      <!-- $axios.defaults.baseURL读取axios的服务器路径 -->
      <img :src="personal.head_img" alt />
      <div class="personal-center">
        <div class="name">
          <span class="iconfont iconxingbienan"></span>
          <!-- 火星网友 -->
          {{personal.nickname}}
        </div>
        <div class="time">2019-10-10</div>
      </div>
      <span class="iconfont iconjiantou1"></span>
    </div>

    <!-- 调用条形组件 -->
    <CellBar label="我的关注" text="关注的用户" />

    <CellBar label="我的跟帖" text="跟帖/回复" />

    <CellBar label="我的收藏" text="文章/视频" />

    <CellBar label="设置" />
  </div>
</template>

<script>
//导入条形组件
import CellBar from "@/components/CellBar";
export default {
  data() {
    return {
      //个人信息
      personal: {}
    };
  },
  components: {
    CellBar
  },

  mounted() {
    //请求个人资料接口
    this.$axios({
      url: "/user/" + localStorage.getItem("user_id"),
      //添加头信息
      headers: {
        Authorization: localStorage.getItem("token")
      }
    }).then(res => {
      // console.log(res)
      const { data } = res.data;

      //保存到data
      this.personal = data;
    
      //如果用户有头像
      if(data.head_img){
          this.personal.head_img = this.$axios.defaults.baseURL +data.head_img;
          console.log(this.data)
      }else{
          this.personal.head_img = "./static/头像.jpg"
      }
    });
  }
};
</script>

<style scoped lang="less">
.personal {
  display: flex;
  padding: 20px 10px;
  justify-content: space-between;
  align-items: center;
  border-bottom: 5px solid #eee;

  img {
    width: 70 /360 * 100vw;
    height: 70 / 360 * 100vw;
    border-radius: 50%;
  }
}

.personal-center {
  flex: 1;
  padding: 0 10px;
}

.name {
  span {
    color: #75b9eb;
  }
}

.time {
  color: #666;
  font-size: 14px;
  margin-top: 5px;
}
</style>