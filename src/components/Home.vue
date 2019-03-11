<template>
  <div class=container>
    <x-header  style="background-color:#409EFF;"
     :right-options="{showMore: true}"  :left-options="{showBack: false}" @on-click-more="showMenus = true">首页</x-header>
    <br>

    <swiper loop auto :list="demo06_list" :index="demo06_index"  @on-index-change="demo06_onIndexChange"></swiper>
    <p>current index: {{demo06_index}}</p>
    
     <grid :cols="4">
      <grid-item :label="('Grid')">
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
    <div v-transfer-dom>
      <actionsheet :menus="menus" v-model="showMenus" show-cancel></actionsheet>
    </div>

     <tabbar>
      <tabbar-item>
        <img slot="icon" src="../assets/home.png">
        <span slot="label">首页</span>
      </tabbar-item>
      <tabbar-item show-dot>
        <img slot="icon" src="../assets/book.png">
        <span slot="label">书籍</span>
      </tabbar-item>
      <tabbar-item selected link="/component/demo">
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
import { Tabbar, TabbarItem, Group, Cell, XHeader, TransferDom, Actionsheet, Swiper, Grid, GridItem, Panel } from 'vux'

const baseList = [{
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vvsr72j20p00gogo2.jpg',
  title: '送你一朵fua'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一辆车'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
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
    Panel
  },
  data () {
    return {
      type: '1',
      showMenus: false,
      demo06_index: 0,
      demo06_list: urlList,
      menus: {
        menu1: '买书籍',
        menu2: '从书库中选择书籍'
      },
      list: [{
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
      footer: {
        title: 'more',
        url: 'http://vux.li'
      }
    }
  },
  methods: {
    demo06_onIndexChange (index) {
      this.demo06_index = index
    }
  }
}
</script>
<style>
.container /deep/ .weui-tabbar {
  position: fixed;
}
</style>