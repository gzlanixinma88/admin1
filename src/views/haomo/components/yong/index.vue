<template>
  <div class="app-container calendar-list-container">
    <h2>用户管理</h2>
    <el-tabs v-model="activeName2" @tab-click="handleClick">
      <el-tab-pane class="chartsPanel" label="用户管理" name="first-ta">
        <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
      </el-tab-pane>
      <el-tab-pane class="chartsPanel" label="用户字段" name="second-ta">
        <button> + 添加字段</button>
        <el-table width="100%" :data="list">
          <el-table-column
            prop="name"
            label="字段名称"
            width="200">
          </el-table-column>
          <el-table-column
            prop="dec"
            label="字段描述"
            width="200">
          </el-table-column>
          <el-table-column
            prop="type"
            label="字段类型"
            width="200">
          </el-table-column>
          <el-table-column
            prop="b"
            label="必填"
            width="100">
          </el-table-column>
          <el-table-column
            prop="c"
            label="常用"
            width="100">
          </el-table-column>
          <el-table-column
            prop="k"
            label="可见"
            width="100">
          </el-table-column>
          <el-table-column
            prop="z"
            label="状态"
            width="100">
          </el-table-column>
        </el-table>
      </el-tab-pane>
    </el-tabs>

  </div>
</template>

<script>
  import Vue from 'vue'
  import axios from 'axios'
  Vue.prototype.$ajax = axios

  export default {
    data () {
      return {
        activeName2: 'first-ta',
        list:[
          {name:'gggg'},
          {name:'gggg'},
          {name:'gggg'},
          {name:'gggg'},
          {name:'gggg'},
          {
            "id": "0aa7435f82614bb8b56af0657a16ee57",
            "username": "test55",
            "loginid": "test55",
            "password": null,
            "mobile": null,
            "email": null,
            "avatar": null,
            "createTime": "2018-05-25 21:27:41",
            "lastUpdateTime": "2018-07-26 09:39:13",
            "lastLoginTime": "2018-08-03 06:47:56",
            "securityLevel": null,
            "type": 0
          },
        ],
        data: [{
          label: '部门',
          children: [{
            label: '信息部',
          },
            {
              label:'财务部'
            },
            {
              label:'人事部'
            }
          ]
        }],
      }
    },
    methods: {
      handleClick: function (tab, event) {
        console.log(event)
        console.log(event.target.getAttribute('id'))  //获取到当前元素的id
      },
      handleNodeClick(data) {
        console.log(data);
      },
      submitForm() {
        this.$ajax({
          method: 'post',
          url: '/hm_users',
        })
      }
    }
  }
</script>
<style lang="sass">

</style>
