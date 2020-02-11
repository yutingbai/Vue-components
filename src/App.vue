<template>
  <a-layout id="components-layout-demo-side" style="min-height: 100vh">
    <a-layout-sider collapsible v-model="collapsed">
      <div class="logo" />
      <a-menu theme="dark" :defaultSelectedKeys="['1']" mode="inline">
        <a-sub-menu key="sub2">
          <span slot="title">
            <a-icon type="team" />
            <span>Team</span>
          </span>
          <a-menu-item key="6">Team 1</a-menu-item>
        </a-sub-menu>
      </a-menu>
    </a-layout-sider>
    <a-layout>
      <a-layout-header style="background: #fff; padding: 0" />
      <a-layout-content style="margin: 0 16px">
        <a-breadcrumb style="margin: 16px 0">
          <a-breadcrumb-item>User</a-breadcrumb-item>
          <a-breadcrumb-item>Bill</a-breadcrumb-item>
        </a-breadcrumb>
        <div :style="{ padding: '24px', background: '#fff', minHeight: '360px' }">



          <message-list :messageList="messageList" @callback="callback"  @search="search"></message-list>




        </div>
      </a-layout-content>
      <a-layout-footer style="text-align: center">Ant Design ©2018 Created by Ant UED</a-layout-footer>
    </a-layout>
  </a-layout>
</template>
<script>
import messageList from "../src/components/messageList/messageList"; // 引入
export default {
  name: "app",
  data() {
    return {
      collapsed: false,
      messageList: [
        {
          title: "用户中心控制台",
          type: "系统消息",
          status: "true",
          avatar:
            "https://zhengxin-pub.bj.bcebos.com/logopic/ac8b826867f384acf46822524cf9bc9f_fullsize.jpg",
          author: "白雨婷",
          datetime: "2020-1-5",
          content:
            "写两个静态页面，一个列表页，主要展示用户收到的消息。主要字段包括标题，内容，来源，状态，类型，发送人，发送时间，操作"
        }
      ]
    };
  },
  components: {
    messageList
  },
  mounted(){
    this.getMessageList();
  },
  methods: {
    getMessageList(){
      this.messageList=[{
          title: "用户中心控制台",
          type: "私信",
          status: "true",
          avatar:
            "https://zhengxin-pub.bj.bcebos.com/logopic/ac8b826867f384acf46822524cf9bc9f_fullsize.jpg",
          author: "白雨婷",
          datetime: "2020-2-5",
          content:
            "写两个静态页面，一个列表页，主要展示用户收到的消息。主要字段包括标题，内容，来源，状态，类型，发送人，发送时间，操作"
        },
        {
          title: "用户中心控制台",
          type: "私信",
          status: "false",
          avatar:
            "https://zhengxin-pub.bj.bcebos.com/logopic/ac8b826867f384acf46822524cf9bc9f_fullsize.jpg",
          author: "白雨婷",
          datetime: "2020-3-5",
          content:
            "写两个静态页面，一个列表页，主要展示用户收到的消息。主要字段包括标题，内容，来源，状态，类型，发送人，发送时间，操作"
        },
        {
          title: "用户中心控制台",
          type: "私信",
          status: "true",
          avatar:
            "https://zhengxin-pub.bj.bcebos.com/logopic/ac8b826867f384acf46822524cf9bc9f_fullsize.jpg",
          author: "白雨婷",
          datetime: "2020-4-5",
          content:
            "写两个静态页面，一个列表页，主要展示用户收到的消息。主要字段包括标题，内容，来源，状态，类型，发送人，发送时间，操作"
        },
        {
          title: "用户中心控制台",
          type: "私信",
          status: "true",
          avatar:
            "https://zhengxin-pub.bj.bcebos.com/logopic/ac8b826867f384acf46822524cf9bc9f_fullsize.jpg",
          author: "白雨婷",
          datetime: "2020-5-5",
          content:
            "写两个静态页面，一个列表页，主要展示用户收到的消息。主要字段包括标题，内容，来源，状态，类型，发送人，发送时间，操作"
        }]
    },
    callback(_this,key) {
      console.log(key);
      _this.form.resetFields();
      this.getMessageList()
    },
    search(data){
      console.log(data)
      this.messageList=[
        {
          title: "用户中心控制台",
          type: "私信",
          status: "true",
          avatar:
            "https://zhengxin-pub.bj.bcebos.com/logopic/ac8b826867f384acf46822524cf9bc9f_fullsize.jpg",
          author: "白雨婷",
          datetime: "2020-4-5",
          content:
            "写两个静态页面，一个列表页，主要展示用户收到的消息。主要字段包括标题，内容，来源，状态，类型，发送人，发送时间，操作"
        },
        {
          title: "用户中心控制台",
          type: "私信",
          status: "true",
          avatar:
            "https://zhengxin-pub.bj.bcebos.com/logopic/ac8b826867f384acf46822524cf9bc9f_fullsize.jpg",
          author: "白雨婷",
          datetime: "2020-5-5",
          content:
            "写两个静态页面，一个列表页，主要展示用户收到的消息。主要字段包括标题，内容，来源，状态，类型，发送人，发送时间，操作"
        }
      ]
    }
  }

};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#components-layout-demo-side .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
}
</style>

