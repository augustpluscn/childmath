<template>
  <div class="home">
    <div v-for="(item,index) in mathArr" :key="index">
      {{item}}
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      mathArr: [],
    };
  },
  components: {},
  mounted() {
    let n = 0;
    let limit = 21;
    let arr = [];
    let x;
    let a;
    let b;
    let z;
    while (n < 50) {
      x = Math.floor(Math.random() * 2);
      a = Math.floor(Math.random() * limit);
      if (x == 0) {
        b = Math.floor(Math.random() * (limit - a));
        z = a + "+" + b + "=";
      } else {
        b = Math.floor(Math.random() * a);
        z = a + "-" + b + "=";
      }
      if (a < 6 && b < 6) {
        continue;
      }
      if (!arr.indexOf(z) > -1) {
        arr.push(z);
        n++;
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
  height: 100%;
  > div {
    width: 50%;
    text-align: center;
    padding: 10px 0;
  }
}
</style>
