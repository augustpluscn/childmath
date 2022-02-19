<template>
  <div class="home">
    <div>
      <div>连减法</div>
      <div>
        <div v-for="(item,index) in lianjian" :key="index">
          {{item}}
        </div>
      </div>
    </div>
    <div>
      <div>破十法</div>
      <div>
        <div v-for="(item,index) in poshi" :key="index">
          {{item}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
function randArr(arr) {
  // 乱序
  for (let i = 1; i < arr.length; i++) {
    const random = Math.floor(Math.random() * (i + 1));
    [arr[i], arr[random]] = [arr[random], arr[i]];
  }
  return arr;
}
export default {
  name: "Jianfa",
  data() {
    return {
      mathArr: [],
    };
  },
  components: {},
  computed: {
    lianjian() {
      return randArr(this.mathArr).slice(0, 26);
    },
    poshi() {
      return randArr(this.mathArr).slice(0, 26);
    },
  },
  mounted() {
    // let start = 11;
    let arr = [];
    for (let index = 11; index < 20; index++) {
      let start = index - 10 + 1;
      for (let n = start; n < 10; n++) {
        arr.push(index + "-" + n + "=");
      }
    }

    this.mathArr = arr;
  },
};
</script>
<style lang="scss">
.home {
  display: flex;
  flex-flow: wrap;
  height: 99%;
  > div {
    height: 100%;
    text-align: center;
    padding: 10px 0;
    display: flex;
    flex-direction: column;
    > div:first-child {
      height: 50px;
      line-height: 50px;
    }
    > div:last-child {
      flex: 1;
      display: flex;
      flex-flow: wrap;
      > div {
        width: 50%;
      }
    }
  }
}
</style>
