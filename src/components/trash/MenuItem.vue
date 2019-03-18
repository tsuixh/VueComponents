<template>
    <div class="menu-item">
      <el-submenu v-if="item.children"
                  :index="item.index"
                  ref="submenu"
      >
        <div slot="title" class="link" @click="handleClick(item.index)" v-if="!item || item.level !== 1">{{item.title}}</div>
        <el-tree :data="tree(item)" :props="config"
                 @node-click="handleNodeClick"
                 v-if="item.level === 1"
                 slot="title"
                 @node-expand="handleExpand"
                 @node-collapse="handleCollapse"
                 @mouseover.native="handleMouseOver(item.index, item.level)"
                 @mouseout.native="handleMouseOut(item.index, item.level)"
                 :node-key="item.index"
                 ref="treeNav"
        ></el-tree>
        <MenuItem v-for="(subItem, index) in item.children" :item="subItem" :key="index" v-on:selected="handleClick"/>
      </el-submenu>
      <el-menu-item v-if="!item.children" :index="item.index" @click="handleClick(item.index)">
        {{item.title}}
      </el-menu-item>
    </div>
</template>

<script>
export default {
  name: 'MenuItem',
  props: {
    item: Object
  },
  data () {
    return {
      config: {
        children: 'children',
        label: 'title'
      },
      openSideNav: false
    }
  },
  methods: {
    handleClick (val) {
      this.$emit('selected', val)
    },
    handleNodeClick (data) {
    },
    data (val) {
      let array = []
      array.push(val)
      return array
    },
    tree (item) {
      let array = []
      array.push(item)
      return array
    },
    handleExpand (obj, node, component) {
      let menuItem = component.$parent.$parent.$parent
      let dom = menuItem.$el
      let marginStr = dom.style.marginBottom
      let margin = parseInt(marginStr) ? parseInt(marginStr) : 0
      let marginBottom = margin + obj.children.length * 40
      dom.style.marginBottom = marginBottom + 'px'
    },
    handleCollapse (obj, node, component) {
      let menuItem = component.$parent.$parent.$parent
      let dom = menuItem.$el
      let marginStr = dom.style.marginBottom
      let margin = parseInt(marginStr)
      let marginBottom = margin - obj.children.length * 40
      dom.style.marginBottom = marginBottom + 'px'
    },
    handleMouseOver (index, level) {
      // console.log(this.$refs.submenu)
      console.log(this.$refs.treeNav)
    },
    handleMouseOut (index, level) {
      // console.log(this.$refs.submenu)
      console.log(this.$refs.treeNav)
    }
  }
}
</script>

<style scoped>
  .menu-item {
    font-size: 16px;
    font-family: Microsoft YaHei,serif;
  }
  .menu-item >>> .el-submenu__icon-arrow {
    display: inline-block;
  }
  .menu-item >>> .el-menu-item{
    height: 40px;
    line-height: 40px;
    font-size: 16px;
  }
  .menu-item >>> .el-submenu__title:hover {
    color: #ca042b;
    background-color: #fafafa;
  }
  li:hover {
    color: #ca042b;
    background-color: #fafafa;
  }
  .menu-item >>> .el-submenu__title {
    height: 40px;
    line-height: 40px;
    font-size: 16px;
  }
  .menu-item >>> .is-active > .el-submenu__title {
    color: #ca042b;
    background-color: #fafafa;
  }
  .menu-item >>> .is-active {
    color: #ca042b;
    background-color: #fafafa;
  }
  .hello >>> .el-tree-node__expand-icon {
    display: none !important;
  }
  li >>> .el-tree-node__content {
    height: 40px;
    line-height: 40px;
    font-size: 16px;
    font-family: Microsoft YaHei sans-serif;
  }
</style>
