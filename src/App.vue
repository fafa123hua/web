<template>
  <div id="app">
    <!-- 导航栏 -->
    <div id="nav">
      <span>Welcome</span>
      <!-- pc导航栏 -->
      <div class="pc">
        <router-link class="pc_a" to="/">主页</router-link>
        <router-link class="pc_a" to="/query">查询</router-link>
        <router-link class="pc_a" to="/update">修改</router-link>
      </div>
      <!-- 移动端导航栏 -->
      <div class="mod">
        <img
          v-if="is_close"
          @click="is_close = !is_close"
          src="./assets/img/mod_menu.png"
        />
        <img
          v-if="!is_close"
          @click="is_close = !is_close"
          src="./assets/img/mod_close.png"
        />
        <div class="nav_mod" v-if="!is_close">
          <router-link class="mod_a" to="/">主页</router-link><br /><br /><br />
          <router-link class="mod_a" to="/query">查询</router-link
          ><br /><br /><br />
          <router-link class="mod_a" to="/update">修改</router-link>
        </div>
      </div>
    </div>

    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {
      // ./assets/img/mod_close.png
      is_close: true,
    };
  },
};
</script>

<style lang="less">
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
// 导航栏
#nav {
  position: relative;
  padding: 10px;
  margin: 0;
  width: 100%;
  height: 40px;
  box-shadow: 0 1px 40px -8px rgba(223, 217, 217, 0.5);
  z-index: 999999;
  text-align: right;
  box-sizing: border-box;

  span {
    position: absolute;
    top: 7px;
    left: 30px;
    font-size: 20px;
    font-weight: 700;
    cursor: pointer;
  }
  // 移动端样式
  .mod {
    position: absolute;
    top: 5px;
    left: 100%;
    transform: translateX(-100%);
    .nav_mod {
      position: absolute;
      width: 100px;
      height: 200px;
      left: 100%;
      transform: translateX(-100%);
      background-color: rgba(197, 132, 132, 0.6);
      z-index: 99;
      text-align: center;
      // 移动端导航栏样式
      .mod_a {
        position: relative;
        margin: 0 10px;
        padding: 5px 10px;
        top: 10%;
        color: #fff;
        font-size: 15px;
        text-decoration: none;
        text-transform: uppercase;
        transition: 0.5s;

        // 点击事件
        &:hover {
          color: #fff;
          background-color: #e91e63;
        }
        &::before {
          content: "";
          position: absolute;
          bottom: 8px;
          left: 8px;
          width: 8px;
          height: 8px;
          border: 3px solid #e91e63;
          border-width: 0 0 3px 3px;
          transition: 0.5s;
          opacity: 0;
        }
        &:hover::before {
          bottom: -6px;
          left: -6px;
          opacity: 1;
        }
        &::after {
          content: "";
          position: absolute;
          top: 8px;
          right: 8px;
          width: 8px;
          height: 8px;
          border: 3px solid #e91e63;
          border-width: 3px 3px 0 0;
          transition: 0.5s;
          opacity: 0;
        }
        &:hover::after {
          top: -6px;
          right: -6px;
          opacity: 1;
        }
      }
    }
  }
  // 隐藏移动端
  .mod {
    display: none;
  }

  // pc a标签端样式
  .pc_a {
    position: relative;
    margin: 0 10px;
    color: #262626;
    font-size: 10px;
    text-decoration: none;
    text-transform: uppercase;
    transition: 0.5s;
    padding: 5px 10px;
    // 点击事件
    &:hover {
      color: #fff;
      background-color: #e91e63;
    }
    &::before {
      content: "";
      position: absolute;
      bottom: 8px;
      left: 8px;
      width: 8px;
      height: 8px;
      border: 3px solid #e91e63;
      border-width: 0 0 3px 3px;
      transition: 0.5s;
      opacity: 0;
    }
    &:hover::before {
      bottom: -6px;
      left: -6px;
      opacity: 1;
    }
    &::after {
      content: "";
      position: absolute;
      top: 8px;
      right: 8px;
      width: 8px;
      height: 8px;
      border: 3px solid #e91e63;
      border-width: 3px 3px 0 0;
      transition: 0.5s;
      opacity: 0;
    }
    &:hover::after {
      top: -6px;
      right: -6px;
      opacity: 1;
    }
  }
  @media only screen and (max-width: 375px) {
    .pc {
      display: none;
    }
    .mod {
      display: block;
    }
  }
}
</style>
