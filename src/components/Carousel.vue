<template>
  <div id="carousel">
    <!-- 图片引入 -->
    <div>
      <img
        src="../assets/img/carousel_1.jpg"
        :class="{ img_opacity: serial == 0, img: true }"
      />
      <img
        src="../assets/img/carousel_2.jpg"
        :class="{ img_opacity: serial == 1, img: true }"
      />
      <img
        src="../assets/img/carousel_3.jpg"
        :class="{ img_opacity: serial == 2, img: true }"
      />
      <!-- 按键 -->
      <div id="carousel_btn">
        <label
          class="carousel_btn"
          v-for="i in maxLen"
          :key="i"
          @mouseenter="btnOver(i - 1)"
          @mouseleave="btnOut(i - 1)"
          ><input type="radio" name="img" @click.stop=""
        /></label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      serial: 0,
      img: null,
      intval: null,
      maxLen: 3,
    };
  },
  created() {
    this.img = setInterval(() => {
      this.serial += 1;
      if (this.serial >= this.maxLen) this.serial = 0;
    }, 3000);
  },
  methods: {
    btnOver(n) {
      //   console.log(1);
      clearInterval(this.img);
      this.serial = n;
    },
    btnOut(n) {
      //   console.log(2);
      this.img = setInterval(() => {
        this.serial += 1;
        if (this.serial >= this.maxLen) this.serial = 0;
      }, 3000);
    },
  },
};
</script>

<style lang='less'>
#carousel {
  position: absolute;
  top: 10%;
  left: 50%;
  transform: translateX(-50%);
  width: 70%;
  height: 30%;
  z-index: -1;
  // 图片变化
  img {
    position: absolute;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: all 1s ease;
  }
  .img_opacity {
    opacity: 1;
  }

  // 按键
  #carousel_btn {
    position: absolute;
    top: 90%;
    width: 100%;
    text-align: center;
    opacity: 0;
    transition: all 0.3s ease;
    &:hover {
      opacity: 0.6;
    }
  }
  .carousel_btn {
    position: relative;
    margin: 7px;
    width: 50px;
    height: 10px;
    border-radius: 10px;
    background-color: #fff;
    display: inline-block;
    transition: all 0.3s ease;

    cursor: pointer;
    input {
      display: none;
    }
    &:hover {
      background-color: gray;
    }
  }
}
</style>