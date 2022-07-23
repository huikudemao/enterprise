<template>
  <div class="home">
<!--    头部-->
    <Header/>
    <div style="display: flex">
      <!--    侧边栏-->
      <Aside/>
      <!--      内容-->
      <router-view style="flex: 1"/>
    </div>
<!--    home-->
<!--    <el-button @click="del">清除</el-button>-->
<!--&lt;!&ndash;    <el-button @click="get1">请求</el-button>&ndash;&gt;-->
<!--    <el-button @click="get2">请求2</el-button>-->
  </div>
</template>

<script>
  import Header from "@/views/Header";
  import Aside from '@/views/Aside'

  import {getHomeIdData} from "../network/home"
export default {
  name: 'Home',
  components:{
    Header,
    Aside
  },
  methods:{
    del(){
      this.$store.commit('del_token'),
        console.log(this.$store.state.token)
      console.log("-----"+sessionStorage.getItem('token'))
      //跳转到当前页
      this.$router.go(0)
    },
   get2(){
     console.log(sessionStorage.getItem('token'))
      getHomeIdData().then(res=>{
        console.log(res)
      }).catch(err => {
        console.log(err)
      })
    }
  }
}
</script>
