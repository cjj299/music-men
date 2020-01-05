<template>
  <div>
      <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      style="height:200px"
    >
    <block v-for="item in imgUrls" :key="item">
      <swiper-item>
        <image :src="item" style="width:100%;"/>
      </swiper-item>
    </block>
   </swiper>
    <i-grid i-class="no-border">
    <i-grid-item @click="goType(grid)" v-for="grid in grids"  :key="grid" i-class="no-border">
        <i-grid-icon>
            <image :src="grid.image" />
            
        </i-grid-icon>
        <i-grid-label>{{grid.title}}</i-grid-label>
    </i-grid-item>
 </i-grid>
 <i-panel :title="title_name">
    <view style="padding: 15px;">
      <i-card v-for="item in top" :key="item" i-class="split"  :extra="item.name" :thumb="item.image">
         <view slot="content">{{item.remark}}</view>
         <view slot="footer">{{item.address}}</view>
    
    </i-card>
   </view>
 </i-panel>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title_name:"热门推荐",
      
     
      top: [
        {name:"陈奕迅",address:"《喜欢一个人》",image:"/static/images/9.jpg",remark:"人生就像马拉松，梦的可能就像一个黑洞一样，只有起点，没有终站，也许我会无条件的喜欢一个人，哪怕只会心烧，也不要成为万圣节的一个传说，那也许只是一个灵魂的独白"},
      ],
       imgUrls: [
         '/static/images/28.jpg',
         '/static/images/29.jpg',
         '/static/images/30.jpg',
         '/static/images/31.jpg',
         '/static/images/32.jpg',
      ],
         indicatorDots: true,
         autoplay: true,
         interval: 5000,
         duration: 1000,

    }
  },


  methods: {
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })

    }
  },

  created () {
  }
}
</script>
<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
div >>> .split {
  margin-bottom: 10pt;
}
</style>

