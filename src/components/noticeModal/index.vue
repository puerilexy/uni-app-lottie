<template>
  <view class="notice-modal" :style="{display: closeFlag ? 'block' : 'none'}">
    <view :class="[coinarea, isShow? 'modal-show' : '']">
      <view class="coin">
          <image class="banner-bg" src="/static/pic-icourt-to-japan-cover.png" />
      </view>
      <view class="lottie-wrap" style="width: 100%; height: 100%; position: absolute; z-index: 888">
          <lottie-miniapp width="500" height="1000"></lottie-miniapp>
      </view>
    </view>
  </view>
</template>

<script>
import LottieMiniapp from '@/lottie-miniapp/component/lottie'
export default {
    name: 'notice-modal',
    components: {
        LottieMiniapp
    },
    props: {
      noticeInfo: {
        type: Object,
        default: () => {
          return {}
        }
      },
      closeFlag: {
        type: Boolean,
        default: false
      }
    },
    data () {
      return {
        isShow: false
      }
    },
    methods: {
    },
    onReady () {
        this.isShow = true
    }
}
</script>

<style>
    .notice-modal{
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background: rgba(255, 255, 125, .1);
        z-index: 999;
    }
    .coinarea{
        width: 100%;
        height: 100%;
    }
    .coin{
        z-index: 998;
        position: absolute;
        left: 0;
        right:0;
        margin: -670rpx auto 0;
        background:#fff;
        width: 670rpx;
        height: 670rpx;
        border-radius: 16rpx;
        transform-origin:0 0;
        transform: rotate(-30deg);
        transition: all .5s cubic-bezier(.17,.89,.32,1.27);
        overflow: visible;
    }

    .banner-bg {
      width: 100%;
      height: 100%;
    }
  
    .d-coin {
        width: 128rpx;
        height: 128rx;
        margin-left: 64rpx;
        margin-top: 64rpx;
        position: absolute;
        /* top: 50%; */
        /* left: 50%; */
        transform-style: preserve-3d;
        transition: all 1s ease-out;
        transition-delay: .3s;
        transform: scale(0) rotateY(0deg);
        /* transform: scale(0); */
        animation: spin .5s cubic-bezier(0.00, 0.00, 0.58, 1.00) infinite;
    }
    .modal-show .coin{
        margin-top: 50%;
        transform: rotate(0);
    }
</style>
