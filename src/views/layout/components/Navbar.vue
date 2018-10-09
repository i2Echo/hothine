<template>
  <div class="nav-container">
    <div class="nav-brand">
      <img class="logo" src="https://placehold.it/40x40" alt="">
      <span class="logo-title">HoThine</span>
    </div>
    <el-menu class="navbar" mode="horizontal">
      <hamburger class="hamburger-container" :toggleClick="toggleSideBar" :isActive="sidebar.opened"></hamburger>
      <!-- <breadcrumb></breadcrumb> -->
      <el-dropdown class="avatar-container" trigger="click">
        <div class="avatar-wrapper">
          <img class="user-avatar" :src="avatar+'?imageView2/1/w/80/h/80'">
          <i class="el-icon-caret-bottom"></i>
        </div>
        <el-dropdown-menu class="user-dropdown" slot="dropdown">
          <router-link class="inlineBlock" to="/">
            <el-dropdown-item>
              Home
            </el-dropdown-item>
          </router-link>
          <el-dropdown-item divided>
            <span @click="logout" style="display:block;">LogOut</span>
          </el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
    </el-menu>
  </div>
  
</template>

<script>
import { mapGetters } from 'vuex'
// import Breadcrumb from '@/components/Breadcrumb'
import Hamburger from '@/components/Hamburger'

export default {
  components: {
    // Breadcrumb,
    Hamburger
  },
  computed: {
    ...mapGetters([
      'sidebar',
      'avatar'
    ])
  },
  methods: {
    toggleSideBar() {
      this.$store.dispatch('ToggleSideBar')
    },
    logout() {
      this.$store.dispatch('LogOut').then(() => {
        location.reload() // 为了重新实例化vue-router对象 避免bug
      })
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.navbar {
  height: 50px;
  line-height: 50px;
  border-radius: 0px !important;
  .hamburger-container {
    line-height: 58px;
    height: 50px;
    float: left;
    padding: 0 10px;
  }
  .screenfull {
    position: absolute;
    right: 90px;
    top: 16px;
    color: red;
  }
  .avatar-container {
    height: 50px;
    display: inline-block;
    position: absolute;
    right: 35px;
    .avatar-wrapper {
      cursor: pointer;
      margin-top: 5px;
      position: relative;
      .user-avatar {
        width: 40px;
        height: 40px;
        border-radius: 10px;
      }
      .el-icon-caret-bottom {
        position: absolute;
        right: -20px;
        top: 25px;
        font-size: 12px;
      }
    }
  }
}
.nav-container {
  position: fixed;
  width: 100%;
  z-index: 9000;
  background-color: #fff;
}
.nav-brand {
  transition: width 0.28s;
  height: 50px;
  width: 180px;
  background-color: #f5f5f5;
  float: left;
  position: relative;
  .logo {
    display: inline-block;
    width: 40px;
    height: 40px;
    margin: 5px;
    background-color: #FFE2E2;
  }
  .logo-title {
    display: inline-block;
    font-size: 24px;
    line-height: 50px;
    position: absolute;
    left: 60px;
    top: 0;
  }
}
.navbar {
    margin-left: 180px;
}

.hideSidebar{
  & .navbar {
    margin-left: 50px;
  }
  & .nav-brand {
    width: 50px;
  }
  & .logo-title {
    display: none;
    position: relative;
    left: 0;
    top: -17px;
  }
} 

.mobile{
  & .nav-brand {
      width: 100%;
      float: none;
      text-align: center;
  }
  & .logo-title {
    display: inline-block;
    position: relative;
    left: 0;
    top: -17px;
  }
  & .navbar {
    margin-left: 0!important;
  }
}

</style>

