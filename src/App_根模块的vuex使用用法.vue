<template>
  <!-- vue2.0需要根元素，vue3.0可以是代码片段 Fragment -->
  <h1>App组件</h1>
  <!-- 1、使用根模块state的数据 -->
  <p>{{$store.state.username}}</p>
  <!-- 1、使用根模块getters的数据 -->
  <p>{{$store.getters.newName}}</p>
  <button @click="updateName">修改名字</button>
</template>

<script>
import { useStore } from 'vuex'
export default {
  name: 'App',
  setup() {
    // 使用vuex仓库
    const store = useStore()
    // 1、使用根模块state的数据
    console.log(store.state.username)
    // 2、使用根模块getters的数据
    console.log(store.getters.newName)
    // 3、提交根模块mutations函数
    function updateName() {
      // store.commit('updateName')
      // 4、调用根模块actives函数
      store.dispatch('updateName')
    }

    return {
      updateName
    }
  }
}
</script>

<style lang="less">
</style>
