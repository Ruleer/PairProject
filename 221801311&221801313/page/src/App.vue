<template>
  <div id="app">
    <a-layout id="components-layout-demo-custom-trigger">
      <a-layout-sider id="asider" v-model="collapsed" :trigger="null" collapsible>
        <div class="logo" />
        <a-menu mode="inline" :default-selected-keys="['index']" @click="route">
          <a-menu-item key="tasks">
            <a-icon type="global" />
            <span>爬虫任务</span>
          </a-menu-item>
          <a-menu-item key="index">
            <a-icon type="unordered-list" />
            <span>论文列表</span>
          </a-menu-item>
          <a-menu-item key="analyze">
            <a-icon type="line-chart" />
            <span>数据分析</span>
          </a-menu-item>
        </a-menu>
      </a-layout-sider>
      <a-layout>
        <a-layout-header style="background: #fff; padding: 0">
          <a-icon
            class="trigger"
            :type="collapsed ? 'menu-unfold' : 'menu-fold'"
            @click="() => (collapsed = !collapsed)"
          />
        </a-layout-header>
        <a-layout-content :style="{ minHeight: '280px' }" >
          <router-view></router-view>
        </a-layout-content>
      </a-layout>
    </a-layout>
  </div>
</template>

<script>
export default {
  data() {
    return {
      collapsed: false,
    };
  },
  methods: {
    route({ item, key, keyPath }) {
      this.$router.push(key);
    }
  },
  mounted() {
    this.$router.push("/index");
  },
};
</script>

<style lang="scss">
#app {
  height: 100%;
  width: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#asider {
  background-color: #ffffff;
  box-shadow: 1px 0 2px #eeeeee;
}

#components-layout-demo-custom-trigger {
  width: 100%;
  height: 100%;
}

#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}

#components-layout-demo-custom-trigger .trigger:hover {
  color: #1890ff;
}

#components-layout-demo-custom-trigger .logo {
  height: 32px;
  background: #aaaaaa;
  margin: 16px;
}
</style>
