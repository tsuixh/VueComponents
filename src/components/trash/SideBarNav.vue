<template>
  <el-card class="box-card">
    <div slot="header" class="clearfix">
      <span>分类</span>
    </div>
    <el-menu :collapse="true" :default-active="catagory.defaultActive" ref="sideNav">
      <MenuItem v-for="(item, index) in catagory.data" :key="index" :item="item" v-on:selected="handleEvent"/>
    </el-menu>
  </el-card>
</template>

<script>
import MenuItem from './MenuItem'
export default {
  name: 'SideNavBar',
  components: {MenuItem},
  props: {
    catagory: Object
  },
  data () {
    return {
    }
  },
  methods: {
    handleEvent (val) {
      this.$emit('selected', val)
    }
  }
}
</script>

<style scoped>
  .box-card {
    width: 100%;
    text-align: left;
    font-size: 16px;
  }
  .box-card >>> .el-card__body {
    padding: 0;
  }
  .box-card >>> .el-menu--collapse {
    width: 100%;
  }
  .box-card >>> .el-card__header {
    height: 50px;
  }
  .box-card >>> .el-menu--collapse {
    margin: 5px 0 5px 0;
  }
</style>
<style>
  .el-menu--popup-right-start {
    margin: 0;
  }
</style>
