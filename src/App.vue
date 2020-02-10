<template>
  <div id="app">
    <message-List :num1="num1" :num2="num2" v-on:getSumFromChild="receiveChildSum"></message-List>
    
    <p>从子组件获取到的值：{{sumFromChild}}</p>
  </div>
</template>

<script>
import messageList from '../src/components/messageList/messageList'; // 引入
export default {
  name: 'app',
  data () {
    return {
      num1: 4,
      num2: 5,
      sumFromChild:0,
    }
  },
  components:{ //注册插件
    messageList
  },
  methods:{
    receiveChildSum(sum){ //自定义事件，接收子组件的和
      this.sumFromChild = sum;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>