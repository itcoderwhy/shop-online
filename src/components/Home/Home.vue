<template>
<div class="home">
  <Header title = "在线商城" />
  <!-- <mt-swipe> -->
  <Loading />
  <div class="lunbotu">
   <mt-swipe :auto="0">
    <mt-swipe-item v-for="img in lunboList" :key="img.id">
      <img :src="img.img" alt="">
    </mt-swipe-item>
    </mt-swipe>
  </div>
  <div class="nine">
    <ul>
      <li>
        <router-link to="/home/newslist">
          <img class="img" src="./menu1.png" alt="">
          <p class="text">新闻资讯</p>
        </router-link>
      </li>
       <li>
        <router-link to="/home/photolist">
          <img class="img" src="./menu2.png" alt="">
          <p class="text">图文分享</p>
       </router-link>
      </li>
       <li>
        <router-link to="/home/goodslist">
          <img class="img" src="./menu3.png" alt="">
          <p class="text">商品展示</p>
      </router-link>
      </li>
       <li>
        <router-link to="home/message">
          <img class="img" src="./menu4.png" alt="">
          <p class="text">留言反馈</p>
      </router-link>
      </li>
       <li>
        <router-link to="/home/search">
          <img class="img" src="./menu5.png" alt="">
          <p class="text">搜索资讯</p>
        </router-link>
      </li>
       <li>
        <router-link to="/home/about">
          <img class="img" src="./menu6.png" alt="">
          <p class="text">关于我们</p>
        </router-link>
      </li>
    </ul>
  </div>
  <BottomBar />
</div>
</template>

<script>
export default {
  data () {
    return {
      lunboList: [] // 轮播图数组
    }
  },
  methods: {
    // 获取轮播图数据
    getLunbo () {
      this.$axios.get('getlunbo').then(res => {
        let data = res.data
        if (data.status === 0) {
          this.lunboList = data.message
        }
      }).catch(err => {
        console.log('获取轮播图数据异常' + err)
      })
    }
  },
  created () {
    this.getLunbo()
  },
  components: {}
}
</script>

<style lang="less" scoped>
  .home {
    position: absolute;
    height: 100%;
    width: 100%;
    .lunbotu {
      .mint-swipe {
        height: 29.9985vh;
          .mint-swipe-items-wrap {
            .mint-swipe-item {
              img {
                width:100%;
                height: 100%;
              }
            }
          }
      }
    }
    .nine {
      padding:0.533333rem 0 0 0;
      ul {
        overflow: hidden;
        li {
          width:33.3%;
          float:left;
          text-align: center;
          margin-top: 0.266667rem;
          .img {
            width: 60px;
            height: 60px;
          }
          .text{
            font-size: 16px;
            color: black;
            margin-top: 0.213333rem;
          }
        }
      }
    }
  }
</style>
