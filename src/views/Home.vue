<template>
  <div id="app">
    <el-container class="my_container">
      <el-header class="my_header">
        <div class="my_sysName">
          JDAPP后台管理
          <i :class="isopen" @click="isOpen"></i>
        </div>
        <div class="my_header_right">
          <span>当前用户：</span>
          <span>退出登录</span>
        </div>
      </el-header>
      <el-container>
        <el-aside class="my_aside" :width="`${asideWidth}px`">
          <el-menu
            :collapse-transition='false'
            :collapse="iscollapse"
            :default-active="defaultActive"
            class="el-menu-vertical-demo"
            @open="handleOpen"
            @close="handleClose"
            background-color="#545c64"
            text-color="#fff"
            active-text-color="#ffd04b"
            router
            style="border :0">
            <el-menu-item index="/goods">
              <i class="el-icon-setting"></i>
              <span slot="title">商品管理</span>
            </el-menu-item>
            <el-menu-item index="/classify">
              <i class="el-icon-menu"></i>
              <span slot="title">分类管理</span>
            </el-menu-item>
          </el-menu>
        </el-aside>
        <el-main class="my_main">
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>

export default {
  data () {
    return {
      iscollapse: true, // 是否折叠导航
      isopen: 'el-icon-s-unfold', // 控制展开折叠的图标
      asideWidth: 64, // 默认折叠时的导航栏的宽度
      defaultActive: window.location.pathname // 当前默认选中的导航
    }
  },
  methods: {
    handleOpen (key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose (key, keyPath) {
      console.log(key, keyPath)
    },
    // 控制展开折叠的图标的点击事件
    isOpen () {
      // 点击，展开导航，再次点击，折叠导航
      this.iscollapse = !this.iscollapse
      // 当导航折叠时，导航栏的宽度为64px，展开时，宽度为200px
      this.asideWidth = this.iscollapse ? 64 : 200
      // 当导航展开和折叠时的图标
      this.isopen = this.iscollapse ? 'el-icon-s-unfold' : 'el-icon-s-fold'
    }
  }
}
</script>

<style scoped>
  #app{
    height: 100%;
  }
  .my_container{
    height: 100%;
  }
 .my_header{
   background:#303133;
   color:#fff;
   display: flex;
   justify-content: space-between;
   align-items: center;
 }
 .my_sysName{
   font-size: 20px;
   font-weight: 500;
 }
 .my_header_right{
   display: flex;
   align-items: center;
   justify-content: space-around;
   width: 200px;
 }
 .my_aside{
   background: #545c64;
   transition: width .3s;
 }
 .my_main{
   background: #E4E7ED;
 }
</style>
