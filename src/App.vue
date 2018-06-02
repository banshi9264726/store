<template>
  <div>
    <my-header></my-header>
    <div class="container-fluid">
      <div class="row">
        <!-- 侧边栏 -->
        <left></left>
        <div class="col-sm-9 col-sm-offset-3 col-md-10 col-md-offset-2 main">
          <!-- 列表 -->
          <router-view></router-view>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// 导入组件
import MyHeader from '@/components/myheader.vue';
import Left from '@/components/left.vue';

export default {
  name: 'App',
  // 添加局部组件
  components: {
    MyHeader,
    Left
  }
};
</script>

<style>

</style>
