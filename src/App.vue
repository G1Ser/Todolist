<template>
  <div class="app" :style="{ 'background-image': `url(${backgroundImage}` }">
    <Header @toggleShade="toggleShade"></Header>
    <MainTodo></MainTodo>
    <Footer></Footer>
    <div v-if="isShadeVisible" class="shade">
      <div class="help">
        <p>1.点击日历可以查看每天的待办事项</p>
        <p>2.当天有待办事项的会有横线提示</p>
        <p>3.在待办事项未完成前，双击可以修改待办事项内容</p>
        <p>4.拖拽待办事项可以完成换位</p>
        <p>5.点击输入框旁边的骨头可以一键全选</p>
        <p>6.点击事件簿下方的信息可以切换事项状态</p>
        <button @click="toggleShade">关闭</button>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import MainTodo from './components/Main/index.vue'
import Footer from './components/Footer.vue'
export default {
  name: 'App',
  components: {
    Header,
    MainTodo,
    Footer
  },
  data() {
    return {
      isShadeVisible: false
    }
  },
  computed: {
    backgroundImage() {
      const hour = new Date().getHours();
      if (hour >= 3 && hour < 9) {
        return require("@/assets/Images/bg.jpg");
        // return require("@/assets/Images/bg1.gif");
      } else if (hour >= 9 && hour < 15) {
        return require("@/assets/Images/bg.jpg");
        // return require("@/assets/Images/bg2.gif");
      } else if (hour >= 15 && hour < 21) {
        return require("@/assets/Images/bg.jpg");
        // return require("@/assets/Images/bg3.gif");
      } else {
        return require("@/assets/Images/bg.jpg");
        // return require("@/assets/Images/bg4.gif");
      }
    }
  },
  methods: {
    toggleShade() {
      this.isShadeVisible = !this.isShadeVisible
    }
  }
}
</script>

<style lang="scss" scoped>
.app {
  width: 100vw;
  height: 100vh;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center center;
  background-size: cover;
  position: relative;
}

.shade {
  display: flex;
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.3);
  justify-content: center;
  align-items: flex-start;

  .help {
    position: relative;
    padding: 1%;
    max-width: 40%;
    margin-top: 20%;
    border-radius: 20px;
    backdrop-filter: blur(2px);
    background-color: rgba(255, 255, 255, 0.8);
    box-shadow: 3px 3px 10px rgba(137, 190, 241, 0.3);

    p {
      font-size: 20px;
      font-weight: 400;
      line-height: 1rem;
      margin-bottom: 1rem;
      font-family: 'Ly';
    }

    button {
      font-size: 15px;
      font-family: 'Ly';
      line-height: 1rem;
      padding: 0.5rem 0.5rem;
      font-weight: bold;
      border: 1px solid #fff;
      border-radius: 20px;
      outline: none;
      cursor: pointer;
      &:hover{
        color: rgb(176,100,123);
      }
    }
  }
}</style>