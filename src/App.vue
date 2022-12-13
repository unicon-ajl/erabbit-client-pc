<template>
  <div class="container">
    <!-- 
      不开启命名空间的，只有state需要指明moduleA，其他的都放到全局了
    -->
    <!-- 1.1、使用A模块的state数据 -->
    <p>{{ $store.state.moduleA.username }}</p>
    <!-- 1.2、使用A模块的getters数据 -->
    <p>{{$store.getters.newName}}</p>


    <!-- 2.1、使用B模块的state数据 -->
    <p>{{ $store.state.moduleB.username }}</p>
    <!-- 2.2、使用B模块的getters数据 -->
    <p>{{$store.getters['moduleB/newName']}}</p>
    <button @click="mutationsFn">mutationsFn</button>
    <button @click="actionsFn">actionsFn</button>
  </div>
</template>

<script>
import { useStore } from 'vuex';

export default {
  name: "App",
  setup() {
    const store = useStore()
    const mutationsFn = () => {
      // 2.3 提交B模块的mutations
      store.commit('moduleB/updateName')
    }

    const actionsFn = () => {
      // 2.4 调用B模块的actions
      store.dispatch('moduleB/updateName')
    }

    return {
      mutationsFn,
      actionsFn
    }
  },
};
</script>

<style lang="less">
</style>
