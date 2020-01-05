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
      grids: [
        {title:"歌手",image:"/static/images/4.png"},
        {title:"电台",image:"/static/images/3.png"},
        {title:"歌曲",image:"/static/images/1.png"},
        {title:"歌单",image:"/static/images/2.png"},
      ],
      top: [
        {name:"陈奕迅",address:"《陪你度过漫长岁月》",image:"/static/images/9.jpg",remark:"You're always with me . 你喜欢我 陪了我这么久 即使我骄傲 自私 做作的时候 你都在――《陪安东尼度过漫长岁月》"},
        {name:"周杰伦",address:"《说好不哭》",image:"/static/images/10.jpg",remark:"我想，你的青春里一定有一首歌是属于Jay的吧。躺在心里，偶而翻出，正好遇上那个情绪，便产生某些新的情感和新的认知。一场青春，一首周杰伦，沮丧时听听，不论是温柔的还是奋进的，总能唱到元气满满。"},
        {name:"华晨宇",address:"《烟火里的尘埃》",image:"/static/images/11.jpg",remark:"我已经了解了这个圈子的游戏规则，我了解这个规则并不是代表我要玩这个游戏，而是只有我了解了规则我才知道如何不在这个游戏里面。"},
        {name:"IU",address:"《除了春天 爱情和樱花》",image:"/static/images/12.jpg",remark:"该曲由IU和High4演唱，过往有为自己的专辑作曲作词的IU，今次是她第一次为其他歌手的歌曲进行填词，这首歌描写了樱花盛开的春天里没有恋人的单身心情。"}
      ],
       imgUrls: [
        'cloud://data-396ee3.6461-data-396ee3/5.jpg',
        '/static/images/6.jpg',
        '/static/images/7.jpg',
        '/static/images/8.jpg',
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
