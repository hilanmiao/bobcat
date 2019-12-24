<template>
  <section class="hero is-fullheight">
    <!-- Hero head: will stick at the top -->
    <div class="hero-head">
      <nav class="navbar">
        <div class="container">
          <div class="navbar-brand">
            <a class="navbar-item has-text-white" href="/">
              <img src="~assets/logo.png" alt="" width="150" style="max-height: fit-content;">
            </a>
          </div>
        </div>
      </nav>
    </div>

    <!-- Hero content: will be in the middle -->
    <div class="hero-body">
      <div class="container">
        <div class="columns">
          <div class="column is-half is-flex column-phone">
            <div class="phone">
              <div class="phone_bg1">
                <div class="phone_bg2">
                  <div class="phone_bg3">
                    <div class="phone_lh">
                      <div class="phone_lh_con">
                        <div class="lh_tiao" />
                        <div class="lh_yuan" />
                      </div>
                    </div>

                    <span class="date_time">{{ time }}</span>

                    <div class="states">
                      <ul class="ul_xinhao">
                        <li />
                        <li />
                        <li />
                        <li />
                      </ul>

                      <div class="wifi1">
                        <div class="wifi2">
                          <div class="wifi3">
                            <div class="wifi4">
                              <div class="wifi5" />
                            </div>
                          </div>
                        </div>
                      </div>

                      <div class="dianliang" />
                    </div>

                    <div class="phone_home" />

                    <iframe style="width: 100%;height: 100%;" :src="gameSrc" frameborder="0" />
                  </div>
                </div>
              </div>

              <div class="jingyin" />
              <div class="yl_jia" />
              <div class="yl_jian" />
              <div class="suoping" />
            </div>
          </div>
          <div class="column column-rule">
            <h1 class="title has-text-white is-size-1">
              游戏规则
            </h1>
            <h2 class="subtitle has-text-white is-6">
              <ul>
                <li>每天登陆，获得三次游戏机会；每天分享朋友圈或好友可增加一次游戏机会</li>
                <li>.......................</li>
                <li>.......................</li>
                <li>.......................</li>
                <li>.......................</li>
              </ul>
            </h2>
            <div class="qrcode-wrapper is-flex">
              <div id="qrcode" class="qrcode" />
            </div>
            <h2 class="subtitle has-text-white has-text-centered">
              扫描二维码可在手机上体验
            </h2>
          </div>
        </div>
      </div>
    </div>

    <!-- Hero footer: will stick at the bottom -->
    <div class="hero-foot" style="padding: 2rem;">
      <div class="content has-text-centered has-text-white">
        <p>
          <strong class="has-text-white">Game</strong> platform maked by <a class="has-text-white" href="https://github.com/hilanmiao">https://github.com/hilanmiao</a>
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      // 时间
      time: '',
      // 二维码配置
      qrcodeObj: {},
      gameSrc: 'http://127.0.0.1:7001/public/upload/web-mobile/index.html'
    }
  },
  mounted () {
    this.init()
    this.getDate()
    setInterval(this.getDate, 1000)
  },
  methods: {
    init () {
      this.qrcodeObj = new window.QRCode('qrcode', {
        text: 'https://github.com/hilanmiao',
        width: 200,
        height: 200,
        // colorDark: '#0f0', // 绿色
        // colorLight: '#fff',
        correctLevel: window.QRCode.CorrectLevel.H
      })
    },
    getDate () {
      const today = new Date()
      this.time = this.twoDigits(today.getHours()) + ':' + this.twoDigits(today.getMinutes())
    },
    twoDigits (val) {
      if (val < 10) {
        return '0' + val
      }
      return val
    }
  }
}
</script>

<style lang="scss" scoped>
  .column-phone {
    justify-content: center;
  }

  .column-rule {
    padding-top: 5em;
  }

  .qrcode-wrapper {
    justify-content: center;
    margin-bottom: 1.5rem;
    .qrcode {
      background: #ffffff;
      padding: 6px;
    }
  }

  @-webkit-keyframes phone {
    0% {
      -webkit-transform: skew(0deg, 0deg) translateY(0px);
    }
    50% {
      -webkit-transform: skew(0deg, 0deg) translateY(5px);
    }
    100% {
      -webkit-transform: skew(0deg, 0deg) translateY(0px);
    }
  }

  @-webkit-keyframes phone_yy {
    0% {
      -webkit-transform: translate(0px, 0px);
      background: rgba(0, 0, 0, 0.2);
      filter: blur(8px);
    }
    50% {
      -webkit-transform: translate(-8px, -8px);
      background: rgba(0, 0, 0, 0.3);
      filter: blur(5px);
    }
    100% {
      -webkit-transform: translate(0px, 0px);
      background: rgba(0, 0, 0, 0.2);
      filter: blur(8px);
    }
  }

  .phone {
    width: 400px;
    height: 800px;
    background: #68686b;
    border-radius: 30px;
    box-sizing: border-box;
    padding: 2px;
    -webkit-transform: skew(0deg, 0deg);
    /*-webkit-animation: phone 4s ease 0s infinite;*/
  }

  .phone:after {
    position: absolute;
    content: "";
    display: block;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.2);
    top: 10px;
    left: 10px;
    z-index: -1;
    border-radius: 18px;
    filter: blur(8px);
    -webkit-animation: phone_yy 4s ease 0s infinite;
  }

  .phone_bg1 {
    width: 100%;
    height: 100%;
    background: #fff;
    border-radius: 30px;
    box-sizing: border-box;
    padding: 0.5px;
  }

  .phone_bg2 {
    width: 100%;
    height: 100%;
    background: #0b0d0c;
    border-radius: 30px;
    box-sizing: border-box;
    padding: 10px;
    box-shadow: inset 14px 0px 10px -15px #fff, inset -14px 0px 10px -15px #fff;
  }

  .phone_bg3 {
    width: 100%;
    height: 100%;
    background: #f8f8f8;
    border-radius: 26px;
    box-sizing: border-box;
    position: relative;

    iframe {
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      border-radius: 26px;
    }
  }

  .phone_lh {
    width: 50%;
    height: 20px;
    background: #0b0d0c;
    margin: 0 auto;
    border-radius: 0px 0px 14px 14px;
    /*position: relative;*/
    position: absolute;
    z-index: 1;
    left: 0;
    right: 0;
  }

  .phone_lh_con {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .phone_lh:before {
    /*position: absolute;
    content: "";
    width: 5px;
    height: 5px;
    background: #0b0d0c;
    left: -5px;
    top: 0px;
    z-index: 9;*/
  }

  .phone_lh:after {
    /*position: absolute;
    content: "";
    width: 5px;
    height: 5px;
    background: #0b0d0c;
    right: -5px;
    top: 0px;
    z-index: 9;*/
  }

  .phone_lh_con:before {
    position: absolute;
    content: "";
    width: 10px;
    height: 10px;
    background: #fff;
    border-radius: 100%;
    left: 10px;
    top: 0px;
    z-index: 10;
  }

  .phone_lh_con:after {
    position: absolute;
    content: "";
    width: 10px;
    height: 10px;
    background: #fff;
    border-radius: 100%;
    right: 10px;
    top: 0px;
    z-index: 10;
  }

  .lh_tiao {
    width: 25%;
    height: 3px;
    border-radius: 5em;
    background: #2d2d2d;
    margin-left: 8px;
    margin-top: 4px;
  }

  .lh_yuan {
    width: 5px;
    height: 5px;
    border-radius: 5em;
    background: #212554;
    margin-left: 8px;
    margin-top: 4px;
  }

  .phone_home {
    width: 32%;
    height: 0.5%;
    border-radius: 5em;
    position: absolute;
    bottom: 1%;
    left: 50%;
    margin-left: -16%;
    background: #0b0d0c;
    z-index: 1;
  }

  .phone_bg3 #text {
    font-size: 18px;
    position: absolute;
    top: 20%;
    left: 0%;
    text-align: center;
    width: 100%;
    font-weight: 600;
  }

  .phone_bg3 .a_user {
    font-size: 10px;
    font-weight: bold;
    position: absolute;
    bottom: 10%;
    left: 50%;
    text-align: center;
    width: 64px;
    margin-left: -32px;
    background: #06F;
    color: #fff;
    border-radius: 5em;
    line-height: 1.5em;
    padding: 3px 0px;
    cursor: pointer;
    transition: all 0.8s ease;
  }

  .phone_bg3 .date_time {
    width: 25%;
    left: 0px;
    position: absolute;
    top: 6px;
    z-index: 111;
    font-size: 13px;
    font-weight: 600;
    text-align: center;
  }

  .states {
    width: 25%;
    right: 1.5px;
    position: absolute;
    top: 4px;
    z-index: 111;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .states .ul_xinhao {
    display: flex;
    align-items: flex-end;
    list-style: none;
  }

  .states .ul_xinhao li {
    width: 3px;
    height: 3px;
    background: #0d0b0c;
    margin-left: 1px;
    list-style: none;
  }

  .states .ul_xinhao li:nth-of-type(2) {
    height: 4px;
  }

  .states .ul_xinhao li:nth-of-type(3) {
    height: 6.5px;
  }

  .states .ul_xinhao li:nth-of-type(4) {
    height: 8.5px;
  }

  .states .dianliang {
    width: 18px;
    height: 10px;
    border: 1px solid #b6b6b6;
    box-sizing: border-box;
    border-radius: 2px;
    margin-left: 0.5px;
    position: relative;
  }

  .states .dianliang:after {
    content: "";
    position: absolute;
    width: 94%;
    height: 88%;
    top: 6%;
    left: 3%;
    box-sizing: border-box;
    background: #0d0b0c;
    border-radius: 2px;
  }

  .states .dianliang:before {
    content: "";
    position: absolute;
    width: 1px;
    height: 4px;
    box-sizing: border-box;
    background: #b6b6b6;
    border-radius: 2px;
    right: -2.5px;
    top: 50%;
    margin-top: -2px;
  }

  .states .wifi1 {
    border-radius: 5em;
    margin-left: 0.5px;
    border: solid transparent;
    border-top-color: #0d0b0c;
    border-width: 2.2px 2.2px;
    display: flex;
    align-items: center;
    justify-content: center;
    transform: translateY(4.5px);
  }

  .states .wifi2 {
    border-radius: 5em;
    border: solid transparent;
    /*border-top-color: #fff;*/
    border-top-color: transparent;
    border-width: 2.15px 2.15px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .states .wifi3 {
    border-radius: 5em;
    border: solid transparent;
    border-top-color: #0d0b0c;
    border-width: 2.1px 2.1px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .states .wifi4 {
    border-radius: 5em;
    border: solid transparent;
    /*border-top-color: #fff;*/
    border-top-color: transparent;
    border-width: 2.05px 2.05px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .states .wifi5 {
    border-radius: 5em;
    border: solid transparent;
    border-top-color: #0d0b0c;
    border-width: 2px 2px;
  }

  .jingyin {
    width: 1.5px;
    height: 3.75%;
    background: #121212;
    position: absolute;
    top: 13.5%;
    left: -1.5px;
    border-radius: 5px 0px 0px 5px;
  }

  .jingyin:after {
    content: "";
    display: block;
    width: 0.8px;
    height: 90%;
    background: rgba(255, 255, 255, 0.8);
    position: absolute;
    left: 0px;
    bottom: 5%;
  }

  .yl_jia {
    width: 1.5px;
    height: 7%;
    background: #121212;
    position: absolute;
    top: 20.75%;
    left: -1.5px;
    border-radius: 5px 0px 0px 5px;
  }

  .yl_jia:after {
    content: "";
    display: block;
    width: 0.5px;
    height: 90%;
    background: rgba(255, 255, 255, 0.6);
    position: absolute;
    right: 0px;
    bottom: 5%;
  }

  .yl_jian {
    width: 1.5px;
    height: 7%;
    background: #121212;
    position: absolute;
    top: 30%;
    left: -1.5px;
    border-radius: 5px 0px 0px 5px;
  }

  .yl_jian:after {
    content: "";
    display: block;
    width: 0.5px;
    height: 90%;
    background: rgba(255, 255, 255, 0.6);
    position: absolute;
    right: 0px;
    bottom: 5%;
  }

  .suoping {
    width: 1.5px;
    height: 11.5%;
    background: #121212;
    position: absolute;
    top: 23%;
    right: -1.5px;
    border-radius: 0px 5px 5px 0px;
  }

  .suoping:after {
    content: "";
    display: block;
    width: 0.5px;
    height: 90%;
    background: rgba(255, 255, 255, 0.6);
    position: absolute;
    left: 0px;
    bottom: 5%;
  }

</style>
