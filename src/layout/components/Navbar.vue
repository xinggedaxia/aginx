<template>
  <div class="navbar">
    <div class="header-main">
      <div class="left-menu">
        <router-link to="/">
          <span class="logo">aginx</span>
        </router-link>
        <div class="menu">
          <router-link to="/">首页</router-link>
          <router-link to="/questions">题库</router-link>
        </div>
      </div>
      <div class="right-menu">
        <!--远程搜索-->
        <remote-search
          v-model="searchVal"
          show-icon
          placeholder="请输入题目名称进行查询"
          class="remote-search"
          @handleSelect="remoteSelect"
        />
<!--        <el-dropdown class="avatar-container" trigger="click">-->
<!--          <div class="avatar-wrapper">-->
<!--            <img :src="avatar+'?imageView2/1/w/80/h/80'" class="user-avatar">-->
<!--            <i class="el-icon-caret-bottom" />-->
<!--          </div>-->
<!--          <el-dropdown-menu slot="dropdown" class="user-dropdown">-->
<!--            <el-dropdown-item divided @click.native="logout">-->
<!--              <span style="display:block;">退出登录</span>-->
<!--            </el-dropdown-item>-->
<!--          </el-dropdown-menu>-->
<!--        </el-dropdown>-->
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import RemoteSearch from '@/components/RemoteSearch'

export default {
  components: {
    RemoteSearch
  },
  computed: {
    ...mapGetters([
      'sidebar',
      'avatar'
    ])
  },
  data() {
    return {
      searchVal: '1234'
    }
  },
  watch: {
    searchVal(newValue, oldValue) {
      console.log(newValue)
    }
  },
  methods: {
    toggleSideBar() {
      this.$store.dispatch('app/toggleSideBar')
    },
    async logout() {
      await this.$store.dispatch('user/logout')
      this.$router.push(`/login?redirect=${this.$route.fullPath}`)
    },
    remoteSelect(item) {
      console.log(item)
    }
  }
}
</script>

<style lang="scss" scoped>
.navbar {
  height: 50px;
  //overflow: hidden;
  position: relative;
  background: #3d444c;
  box-shadow: 0 1px 4px rgba(0,21,41,.08);

  .header-main{
    display: flex;
    justify-content: space-between;
    width: 1200px;
    height: 50px;
    margin: 0 auto;
    .logo{
      width: 70px;
      line-height: 50px;
      height: 100%;
      font-size: 22px;
      font-weight: bold;
      font-style: italic;
      color: #E6A23C;
    }
    .left-menu{
      display: flex;
      .menu{
        display: flex;
        a{
          color: #ccc;
          font-size: 16px;
          line-height: 50px;
          padding: 0 10px
        }
        a.router-link-exact-active{
          color: white;
        }
      }

    }
    .right-menu {
      display: flex;
      height: 100%;
      line-height: 50px;

      &:focus {
        outline: none;
      }

      .remote-search{
        ::v-deep input.el-input__inner{
          background: #31363e;
          border: none;
          color:white;
        }
      }

      .right-menu-item {
        display: inline-block;
        padding: 0 8px;
        height: 100%;
        font-size: 18px;
        color: #5a5e66;
        vertical-align: text-bottom;

        &.hover-effect {
          cursor: pointer;
          transition: background .3s;

          &:hover {
            background: rgba(0, 0, 0, .025)
          }
        }
      }

      .avatar-container {
        margin-right: 30px;

        .avatar-wrapper {
          margin-top: 5px;
          position: relative;

          .user-avatar {
            cursor: pointer;
            width: 40px;
            height: 40px;
            border-radius: 10px;
          }

          .el-icon-caret-bottom {
            cursor: pointer;
            position: absolute;
            right: -20px;
            top: 25px;
            font-size: 12px;
          }
        }
      }
    }

  }

}
</style>
