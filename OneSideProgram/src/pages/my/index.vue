<template>
  <div class="wrap">
    <header>
      <image src="/static/images/logo.png" lazy-load="false"></image>
      <p>176****6605</p>
    </header>
    <ul>
      <li>
        <icon type="waiting" size="24px" />
        <span>
          我的面试
        </span>
        <span>〉</span>
      </li>
    </ul>
    <div class="phone" v-if="showPhoneDialog">
      <p>为了更好的使用我们的服务，我们需要获取你的手机号码</p>
      <button open-type="getPhoneNumber" @getphonenumber="getPhoneNumber">允许获取手机号</button>
    </div>
  </div>
</template>

<script>
import {getLocation, getAuth} from '@/utils/index.js'
import {mapState, mapMutations} from 'vuex'

export default {
  data () {
    return {
      showPhoneDialog: true
    }
  },

  computed: {
    ...mapState({
      info: state=>state.info
    })
  },

  methods: {
    getPhoneNumber(e){
      console.log('e...', e);
    }
  },

  onShow() {
    if (!this.info.phone){
      this.showPhoneDialog = false;
    }
  }
}
</script>

<style lang="scss" scoped>
header{
  background: #F4F6F9;
  width: 100%;
  height: 400rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  image{
    width: 100rpx;
    height: 100rpx;;
  }
}
.phone{
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0, .3);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  p{
    width: 60%;
    background: #fff;
  }
  button{
    width: 60%;
  }
}
</style>
