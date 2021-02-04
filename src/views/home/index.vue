<template>
  <div class="home-container">
   <div class="main">
     <div class="header-sort">
     <ul>
       <li><a :class="{'current-mode':sort==='hot' }" href="javascript:void(0);">热门</a></li>
       <li><a :class="{'current-mode':sort==='new' }" href="javascript:void(0);">最新</a></li>
     </ul>
   </div>
     <div class="article-list">
       <article-overview v-for="article in articleList" :key="article.id" :article-data="article" />
       <div v-show="articleList.length===0" class="no-data">
         暂无数据，快来写文章 ~
       </div>
     </div>
   </div>
    <div class="slider-bar">
        广告位招商
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import ArticleOverview from './components/ArticleOverview'

export default {
  name: 'Home',
  components: {
    ArticleOverview
  },
  data() {
    return {
      sort: 'hot',
      articleList: [
        {
          id: '1',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '12',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '13',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '14',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '15',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '16',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '17',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '18',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '19',
          author: 'xingge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: false// 是否已经赞过
        },
        {
          id: '20',
          author: 'qiangge',
          time: '1小时前',
          tag: '职场规划',
          title: '一个合格的初级前端工程师需要掌握的模块笔记',
          likes: 999,
          currentLike: true// 是否已经赞过
        }
      ]
    }
  },
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  created() {
  }
}
</script>

<style lang="scss" scoped>
.home-container {
  display: flex;
  justify-content: center;
  margin-top: 20px;
  .main{
    margin-right: 20px;
    width: 800px;
    background: #fff;
    .header-sort{
      height: 50px;
      ul{
        display: flex;
        padding: 0;
        height: 50px;
        align-items: center;
        list-style: none;
        border-bottom: 1px solid hsla(0,0%,59.2%,.2);;
        li{
          display: flex;
          width: 70px;
          align-items: center;
          justify-content: center;
          &:not(:last-child){
            border-right: 1px solid hsla(0,0%,59.2%,.2);
          }
          a{
            &.current-mode{
              color: #007fff;
            }
          }
        }
      }
    }
    .article-list{
      padding-bottom: 50px;
      .no-data{
        height: 50px;
        line-height: 50px;
        text-align: center;
      }
    }
  }
  .slider-bar{
    width: 250px;
    height: 200px;
    background: #fff;
    text-align: center;
    line-height: 200px;
  }
}
</style>
