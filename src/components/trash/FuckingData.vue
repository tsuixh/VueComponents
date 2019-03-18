<template>
  <SideNavBar v-on:selected="handleSelect" :catagory="catagory" style="width: 400px;"></SideNavBar>
</template>

<script>
import SideNavBar from './SideNavBar'
export default {
  name: 'unknow',
  data () {
    return {
      catagory: {
        defaultActive: null,
        data: [
          {
            title: '全部分类',
            index: 'all',
            level: 1
          },
          {
            title: '交付场景',
            index: '1',
            level: 1,
            children: [
              {
                title: '5G',
                index: '1-1',
                level: 2,
                children: [
                  {
                    level: 3,
                    title: '移动',
                    index: '1-4-1'
                  },
                  {
                    level: 3,
                    title: '电信',
                    index: '1-4-2'
                  },
                  {
                    level: 3,
                    title: '联通',
                    index: '1-4-3'
                  },
                  {
                    level: 3,
                    title: '总体组',
                    index: '1-4-4'
                  }
                ]
              },
              {
                level: 2,
                title: 'IDC',
                index: '1-2'
              },
              {
                level: 2,
                title: '家宽集客',
                index: '1-3'
              },
              {
                level: 2,
                title: '商解',
                index: '1-4'
              },
              {
                level: 2,
                title: 'MBB',
                index: '1-5'
              },
              {
                level: 2,
                title: 'FBB',
                index: '1-6'
              },
              {
                level: 2,
                title: 'CS',
                index: '1-7'
              },
              {
                level: 2,
                title: 'LS',
                index: '1-8'
              },
              {
                level: 2,
                title: 'NFV',
                index: '1-9'
              },
              {
                level: 2,
                title: 'MCE',
                index: '1-10'
              },
              {
                level: 2,
                title: '软件',
                index: '1-11'
              }
            ]
          },
          {
            title: '流程',
            index: '2',
            level: 1,
            children: [
              {
                title: '请假',
                index: '2-1'
              }
            ]
          },
          {
            level: 1,
            title: 'DOC',
            index: '3'
          },
          {
            level: 1,
            title: '经营',
            index: '4'
          },
          {
            level: 1,
            title: '现场管理',
            index: '5'
          },
          {
            level: 1,
            title: '资源',
            index: '6'
          },
          {
            level: 1,
            title: '读书荟',
            index: '7'
          }
        ]
      }
    }
  }
</script>
