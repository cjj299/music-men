<template>
  <div>
    <view class="userinfo">
    <view class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>
    <i-panel title="我是音乐人，我要推荐！！！">
      <i-input :value="name" @change="changeName($event)" title="歌曲名" autofocus placeholder="请输入歌名" maxlength="20" />
      <i-input :value="singer" @change="changeAddress($event)" title="歌手" placeholder="请输入歌手" maxlength="30" />
      <i-input :value="singer" @change="changeAddress($event)" title="专辑名称" placeholder="请输入专辑" maxlength="30" />
      <i-input :value="reason" @change="changeReason($event)" title="推荐理由" placeholder="请输入推荐理由" maxlength="50" />
    </i-panel>
    <i-button @click="handleClick" type="warning" size="default">我要推荐┗|｀O′|┛ 嗷~~</i-button>
    <view class="tips">宝藏音乐人专用小程序，如果你发现有听的宝藏歌曲请分享给我们！！！</view>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name:"",
      address:"",
      reason:""
    }
  },
  methods: {
    changeName (event) {
      this.name = event.mp.detail.detail.value
    },
    changeReason (event) {
      this.reason = event.mp.detail.detail.value
    },
    changeAddress (event) {
      this.address = event.mp.detail.detail.value
    },
    handleClick () {
      if (this.name && this.reason && this.address) {
        wx.showToast({
          title: '推荐了' + this.name,
          icon: 'success',
          duration: 2000
        })
        // TODO:将推荐数据提交到云数据库
      } else {
        wx.showToast({
          title: '信息不完整',
          icon: 'none',
          duration: 2000
        })
      }
    }
  },
  created () {
  }
}
</script>

<style scoped>
.userinfo {
  position: relative;
  width: 750rpx;
  height: 320rpx;
  color: #666;
  display: flex;
  flex-direction: column;
  align-items: center;
}
 
.userinfo-avatar {
  overflow:hidden;
  display: block;
  width: 160rpx;
  height: 160rpx;
  margin: 20rpx;
  margin-top: 50rpx;
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}
.tips {
  padding: 20pt;
  font-size: 10pt;
  color:darkorange;
}
</style>