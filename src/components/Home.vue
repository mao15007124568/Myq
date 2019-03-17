<template>
  <div class=container>
    <x-header  style="background-color:#409EFF;"
     :right-options="{showMore: true}"  :left-options="{showBack: false}" @on-click-more="login">首页</x-header>
    <br>

    <swiper loop auto :list="demo06_list" :index="demo06_index"  @on-index-change="demo06_onIndexChange"></swiper>
    
     <grid :cols="4">
      <grid-item list="/login" :label="('Grid')">
        <img slot="icon" src="../assets/paper_plane.png">
      </grid-item>
       <grid-item :label="('Grid')">
        <img slot="icon" src="../assets/vux_logo.png">
      </grid-item>
       <grid-item :label="('Grid')">
        <img slot="icon" src="../assets/protractor.png">
      </grid-item>
       <grid-item :label="('Grid')">
        <img slot="icon" src="../assets/lockers.png">
      </grid-item>
      <grid-item :label="('Grid')">
        <img slot="icon" src="../assets/book.png">
      </grid-item>
      <grid-item :label="('Grid')">
        <img slot="icon" src="../assets/book.png">
      </grid-item>
      <grid-item :label="('Grid')">
        <img slot="icon" src="../assets/book.png">
      </grid-item>
      <grid-item :label="('Grid')">
        <img slot="icon" src="../assets/book.png">
      </grid-item>
    </grid>

    <panel :header="'推荐'" :list="list" :footer="footer" :type="type"></panel>

     <tabbar>
      <tabbar-item>
        <img slot="icon" src="../assets/home.png">
        <span slot="label">首页</span>
      </tabbar-item>
      <tabbar-item show-dot link="/now" >
        <img slot="icon" src="../assets/book.png">
        <span slot="label">附近</span>
      </tabbar-item>
      <tabbar-item selected>
        <img slot="icon" src="../assets/application.png">
        <span slot="label">附近</span>
      </tabbar-item>
      <tabbar-item badge="2">
        <img slot="icon" src="../assets/message.png">
        <span slot="label">我的</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>

<script>
import { Tabbar, TabbarItem, Group, Cell, XHeader, TransferDom, Actionsheet, Swiper, Grid, GridItem, Panel, Masker } from 'vux'

const baseList = [{
  url: 'javascript:',
  img: 'src/assets/cheyou.png',
  title: '送你一朵fua'
}, {
  url: 'javascript:',
  img: 'src/assets/lanjian.png',
  title: '送你一辆车'
}, {
  url: 'javascript:',
  img: 'src/assets/shenbao.png',
  title: '送你一次旅行',
  fallbackImg: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw50iwj20ff0aaaci.jpg'
}]

const urlList = baseList.map((item, index) => ({
  url: 'http://m.baidu.com',
  img: item.img,
  fallbackImg: item.fallbackImg,
  title: `(可点击)${item.title}`
}))

export default {
  directives: {
    TransferDom
  },
  components: {
    Tabbar,
    TabbarItem,
    Group,
    Cell,
    XHeader,
    Actionsheet,
    Swiper,
    Grid,
    GridItem,
    Panel,
    Masker
  },
  data () {
    return {
      list: [{
        title: '洗颜新潮流！人气洁面皂排行榜',
        img: 'https://cdn.xiaotaojiang.com/uploads/82/1572ec37969ee263735262dc017975/_.jpg'
      }, {
        title: '美容用品 & 日用品（上）',
        img: 'https://cdn.xiaotaojiang.com/uploads/59/b22e0e62363a4a652f28630b3233b9/_.jpg'
      }, {
        title: '远离车内毒气，日本车载空气净化器精选',
        img: 'https://cdn.xiaotaojiang.com/uploads/56/4b3601364b86fdfd234ef11d8712ad/_.jpg'
      }],
      list2: [{
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        fallbackSrc: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题一',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: '/component/cell'
      }, {
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        fallbackSrc: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题一',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: '/component/cell'
      }, {
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        fallbackSrc: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题一',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: '/component/cell'
      }, {
        src: 'http://www.zhantengwang.com/uploads/allimg/181016/1-1Q016144920196.jpg',
        title: '标题二',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: {
          path: '/component/radio',
          replace: false
        },
        meta: {
          source: '来源信息',
          date: '时间',
          other: '其他信息'
        }
      }],
      type: '1',
      demo06_index: 0,
      demo06_list: urlList,
      menus: {
        menu1: '买书籍',
        menu2: '从书库中选择书籍'
      },
      footer: {
        title: 'more',
        url: 'http://vux.li'
      }
    }
  },
  methods: {
    demo06_onIndexChange (index) {
      this.demo06_index = index
    },
    login () {
      this.$router.push('/login')
    }
  }
}
</script>
<style lang="less">
.container /deep/ .weui-tabbar {
  position: fixed;
}
.m-img {
  padding-bottom: 33%;
  display: block;
  position: relative;
  max-width: 100%;
  background-size: cover;
  background-position: center center;
  cursor: pointer;
  border-radius: 2px;
}

.m-title {
  color: #fff;
  text-align: center;
  text-shadow: 0 0 2px rgba(0, 0, 0, .5);
  font-weight: 500;
  font-size: 16px;
  position: absolute;
  left: 0;
  right: 0;
  width: 100%;
  text-align: center;
  top: 50%;
  transform: translateY(-50%);
}

.m-time {
  font-size: 12px;
  padding-top: 4px;
  border-top: 1px solid #f0f0f0;
  display: inline-block;
  margin-top: 5px;
}
</style>