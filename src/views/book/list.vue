<template>
  <el-menu
    default-active="2"
    background-color="#545c64"
    text-color="#fff"
    active-text-color="#ffd04b"
    mode="vertical"
    :unique-opened="true"
    :collapse="isCollapse"
    :collapse-transition="false"
    @open="handleOpen"
    @close="handleClose"
    @select="handleSelect"
  >
    <el-submenu index="1">
      <template slot="title">
        <i class="el-icon-user" />
        <span>第一步：拿Token</span>
      </template>
      <el-menu-item-group>
        <template>
          <i class="el-icon-check" />
          <span>拿到Token</span>
        </template>
        <el-menu-item index="1-1">
          根据用户角色生成动态路由
        </el-menu-item>
      </el-menu-item-group>
      <el-menu-item-group>
        <template>
          <i class="el-icon-close" />
          <span>没拿到Token</span>
        </template>
        <el-menu-item index="1-2">
          whiteList有该roles，直接访问
        </el-menu-item>
        <el-menu-item index="1-3">
          whiteList没有该roles，登录才能访问
        </el-menu-item>
      </el-menu-item-group>
    </el-submenu>
    <el-submenu index="2">
      <template slot="title">
        <i class="el-icon-message-solid" />
        <span>动态路由及权限校验</span>
      </template>
      <el-menu-item-group>
        <template>
          <i class="el-icon-check" />
          <span>√ 拿到Token</span>
        </template>
      </el-menu-item-group>
      <el-menu-item-group>
        <template>
          <i class="el-icon-close" />
          <span>× 没拿到Token</span>
        </template>
      </el-menu-item-group>

    </el-submenu>
  </el-menu>
</template>

<script>
export default {
  data() {
    return {
      isCollapse: false
    }
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log('handleSelect', key, keyPath)
    },
    handleOpen(key, keyPath) {
      console.log('handleOpen', key, keyPath)
    },
    handleClose(key, keyPath) {
      console.log('handleClose', key, keyPath)
    }
  }
}
</script>

<style lang="stylus" scoped></style>
