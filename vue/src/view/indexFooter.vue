<template>
    <footer>
          <div class="content flex">
            <dl>
              <dt>
                <img src="@/assets/images/logo6.png" alt="">
              </dt>
            </dl>
            <dl>
              <dt>{{$t('foo.about')}}</dt>
              <!-- <router-link to="/c2c" tag="dd">c2c交易</router-link>
              <router-link to="/leverdealCenter" tag="dd">合约交易</router-link> -->
              <dd v-for="item in footFrist" @click="goDetail(item.id)" :key="item">{{item.title}}</dd>
            </dl>
            <dl>
              <dt>{{$t('foo.support')}}</dt>
              <dd v-for="item in footSecond" @click="goDetail(item.id)" :key="item">{{item.title}}</dd>
              <!-- <router-link to="/components/login" tag="dd">登录</router-link>
              <router-link to="/components/register" tag="dd">注册</router-link>
              <router-link to="/forgetPwd" tag="dd">找回密码</router-link> -->
            </dl>
            <dl>
              <dt>{{$t('foo.contact')}}</dt>
              <dd class="felx alcenter center">
                <!-- <div class="flex alcenter center">
                  <img src="../assets/images/email.png" alt="">
                  <span class="ml5">BBANK@hotmail.com</span>
                </div> -->
                <ul class="concat_ul flex tc end">
                  <li class="wechat-box">
                    <img src="../assets/images/footer/wechat.png" alt="">
                    <img src="../assets/images/footer/weimg.jpg" alt="" class="weimg">
                  </li>
                  <li>
                    <img src="../assets/images/footer/facebook.png" alt="">
                  </li>
                  <li>
                    <img src="../assets/images/footer/twitter.png" alt="">
                  </li>
                  <li>
                    <img src="../assets/images/footer/youtube.png" alt="">
                  </li>
                </ul>
                <ul class="concat_ul flex tc mt10">
                  <li>
                    <img src="../assets/images/footer/telegram.png" alt="">
                  </li>
                  <li>
                    <img src="../assets/images/footer/medium.png" alt="">
                  </li>
                  <li>
                    <img src="../assets/images/footer/ins.png" alt="">
                  </li>
                  <li>
                    <img src="../assets/images/footer/weibo.png" alt="">
                  </li>
                </ul>                
               </dd>

            </dl>
          </div>
          <p class="flex column center mt20 tc ft12">
            <span class="white ft20">BBANK</span>
            ©2014-2018 BBANK,All Rights Reserved
            </p>
        </footer>
</template>
<script>
export default {
  name: "indexFooter",
  data() {
    return {
      footFrist:[],
      footSecond:[],
    };
  },
  created() {
  },
  mounted() {

    this.aboutUs();
    this.help();
  },
  methods: {
    // 公告详情
    goDetail(id) {
      var id = id;
      this.$router.push({
        name: "noticeDetail",
        query: { id: id }
      });
    },
    aboutUs(){
      var that = this;
      this.$http.post("/api/news/list",{"c_id":9}).then(res => {
        if (res.data.type == "ok") {
             var list = res.data.message.list;
             if (list.length > 2) {
            that.footFrist = list;
          } else {
            that.footFrist = list;
          }
        } else {
          // layer.msg(res.message);
        }
      });
    },
    help(){
      var that = this;
      this.$http.post("/api/news/list",{"c_id":10}).then(res => {
        if (res.data.type == "ok") {
             var list = res.data.message.list;
             if (list.length > 2) {
            that.footSecond = list;
          } else {
            that.footSecond = list;
          }
        } else {
          // layer.msg(res.message);
        }
      });
    }
  }
};
</script>


<style scoped lang='scss'>

footer{
  width: 100%;
  // background: #111114;
  background: #000;
  padding: 80px 0 0 0;
  text-align: center;
  .content{
    width: 1200px;
    margin: 0 auto;
    justify-content: space-between;
    border-top: 1px solid #42f1eb;
    padding-top: 50px;
    dl{
      flex: 1;
      text-align: center;
      dt{
        font-size: 16px;
        color: #fff;
        margin-bottom: 10px;
        // text-align: left;
      }
      dd{
        font-size: 14px;
        color: #a7b7c7;
        line-height: 24px;
        // text-align: left;
        cursor: pointer;
        padding-top: 10px;
        &:hover{
          color: #fff;
        }
      }
    }
  }
  p{
    // border-top: 1px solid #303035;
    height: 120px;
    color: #727b92;
  }
}
.concat_ul{
  justify-content: flex-end;
  li{
    width: 32px;
    height: 32px;
    background: #303e63;
    border-radius: 50%;
    margin-right: 10px;
    img{
      width: 20px;
      height: 20px;
      margin-top: 6px;
    }
  }
  li:hover{
    background: #5697f4;
  }
  .wechat-box{
    position: relative;
    .weimg{
      width: 140px;
      height: 140px;
      position: absolute;
      top: -155px;
      left: -60px;
      border: 5px solid #fff;
      display: none;
    }
  }
  .wechat-box:hover .weimg{
      display: block;
  }
}
</style>





// WEBPACK FOOTER //
// src/view/indexFooter.vue