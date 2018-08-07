<template>
  <div class="app-container calendar-list-container">
    <h2>用户管理</h2>
    <el-tabs v-model="activeName2" @tab-click="handleClick">
      <el-tab-pane class="chartsPanel" label="用户管理" name="first-ta">
        <el-tree
          :props="props"
          lazy
          @check-change="handleCheckChange">
        </el-tree>
      </el-tab-pane>
      <el-tab-pane class="chartsPanel" label="用户字段" name="second-ta">
        <button> + 添加字段</button>
        <el-table width="100%" :data="list">
          <el-table-column
            prop="username"
            label="字段名称"
            width="200">
          </el-table-column>
          <el-table-column
            prop="logoid"
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
  Vue.prototype.$axios = axios;

  export default {
    data () {
      return {
        activeName2: 'first-ta',
        list:[],
        props: {
          label:'name',
          children:'zones'
        },
        count:"1"
      }
    },
    created(){
      this.$axios.get('http://api.haomo-studio.com/org/hm_users')
        .then((e)=> {
          this.list = e.data
        })
      this.$axios.get('http://api.haomo-studio.com/org/departments')
        .then((e)=> {
          this.props = e.data
          console.log(this.props)
        })
    },
    methods: {
      handleClick: function (tab, event) {
        console.log(event)
        console.log(event.target.getAttribute('id'))  //获取到当前元素的id
      },
      handleNodeClick(data) {
        console.log(data);
      },
      handleCheckChange(data, checked, indeterminate) {
        console.log(data, checked, indeterminate);
      }
    }
  }
</script>
<style lang="sass">

</style>
