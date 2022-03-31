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
            <van-cell title="手机号：17395652040"  />
            <van-cell title="邮箱：1620889647@qq.com"  />
        </div>
      </div>
      <!-- 顶部区域 -->
        <!-- 轮播图 -->
        <van-swipe class="my-swipe" autoplay="2000"  indicator-color="white" v-if="this.win.width <1000">
          <van-swipe-item>1</van-swipe-item>
          <van-swipe-item>2</van-swipe-item>
          <van-swipe-item>3</van-swipe-item>
          <van-swipe-item>4</van-swipe-item>
        </van-swipe>

        <v-carousel v-if="this.win.width>1000">
          <v-carousel-item
            v-for="(item,i) in items"
            :key="i"
            :src="item.src"
            reverse-transition="fade-transition"
            transition="fade-transition"
          ></v-carousel-item>
        </v-carousel>
        <!-- 轮播图 -->
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
      ]
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
      console.log(this.win.width)
      console.log(this.win.height)
    }
  }
}
</script>

<style lang="less" scoped>
.home{
   height: 60px;
    background-color: #000;
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
    .right_call{
        position: absolute;
        bottom:-90px;
        right: 0;
        border: solid 1px  #000;
        border-radius: 10px;
        margin: 0;
        padding: 0;
        .van-cell {
          border-radius: 10px;
        }
    }
  }
}
.banner{
  width: 80%;
  margin: 0 auto;
}
 .my-swipe .van-swipe-item {
    color: #fff;
    font-size: 20px;
    line-height: 150px;
    text-align: center;
    background-color: #39a9ed;
  }
</style>
