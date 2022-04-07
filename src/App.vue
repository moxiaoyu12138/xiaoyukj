<template>
  <v-app>
    <div class="home">
      <!-- 顶部区域 -->
      <div class="home_top banner">
        <div class="left">
          小雨科技
        </div>
        <div class="right" @click="onCall">
          <van-icon name="phone-o"/>
          <span>联系我</span>
        </div>
        <div class="right_call" v-if="this.call">
            <van-cell title="手机号：17395652040" @click="callme"  />
            <van-cell title="邮箱：1620889647@qq.com" @click="email" />
        </div>
      </div>
      <!-- 顶部区域 -->
        <!-- 轮播图 -->
        <van-swipe class="my-swipe"   indicator-color="white" v-if="this.win.width <1000">
          <van-swipe-item v-for="(item,i) in items" :key="i">
            <img :src="item.src" id="item-img">
          </van-swipe-item>
        </van-swipe>

        <v-carousel v-if="this.win.width>1000"
          height="400px"
          interval="6000"
          >
          <v-carousel-item
            v-for="(item,i) in items"
            :key="i"
            :src="item.src"
            reverse-transition="fade-transition"
            transition="fade-transition"
          ></v-carousel-item>
        </v-carousel>
        <!-- 轮播图 -->
      <!-- 主体内容区域 -->
      <div class="home_main">
        <!-- 三个分类的div盒子 -->
         <van-tabs v-model="active"
         title-active-color="#00c6ff"
         title-inactive-color="#005bea"
         title="作品集"
         >
         <!-- 作品集 -->
          <van-tab title="h5">作品集</van-tab>
          <van-tab title="css">css</van-tab>
          <van-tab title="js">js</van-tab>
          <van-tab title="vant">vant</van-tab>
          <van-tab title="vue">vue</van-tab>
        </van-tabs>
      </div>
    </div>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data () {
    return {
      call: false,
      win: {
        width: '',
        height: ''
      },
      items: [
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/sky.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg'
        }
      ],
      tab: null,
      active: 0
    }
  },
  created () {
    this.query()
  },
  methods: {
    onCall () {
      this.call = !this.call
    },
    // 获取屏幕宽高用于轮播图显示
    query () {
      this.win.width = document.body.offsetWidth
      this.win.height = window.screen.availWidth
    },
    callme () {
      window.location.href = 'tel:17395652040'
    },
    // 发送邮件给我
    email () {
      window.location.href = 'mailto:1620889647@qq.com'
    }
  }
}
</script>

<style lang="less" scoped>
.home{

   height: 60px;
    // background-color: #000;
    //渐变色蓝到黑
    //渐变黑
    background:
    linear-gradient(to right,#00c6ff 0%,#005bea 20%, #00c6ff 40%,#005bea 60%,#00c6ff 80%,#005bea 100%);
  .home_top{
    position: relative;
    display: flex;
    justify-content: space-between;
    color: #fff;
    .left{
      font-size: 30px;
      line-height: 60px;
    }
    .right{
      line-height: 60px;
    }
    .van-cell{
      // 背景色透明
      background-color: transparent;
      color: #fff;
    }
    .right_call{
        position: absolute;
        bottom:-90px;
        right: 0;
        border: solid 1px  #000;
        border-radius: 10px;
        margin: 0;
        padding: 0;
        z-index: 22;
        .van-cell {
          border-radius: 10px;
        }
    }
  }
 /deep/ .home_main{
    div.van-tabs__line{
      background-color: #005bea;
    }
  }
}
 .van-swipe-item{
   height: 200px;
     #item-img{
       width: 100%;
       height: 200px;

     }
 }
.card_main{
  margin-top: 20px;
}
.banner{
  width: 80%;
  margin: 0 auto;
}
 .my-swipe .van-swipe-item {
    font-size: 20px;
    line-height: 150px;
    text-align: center;
    background-color: #39a9ed;
  }

</style>
