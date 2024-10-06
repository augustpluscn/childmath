<template>
  <div class="home">
    <div>
      <div v-for="(item, index) in mathArr" :key="index">
        {{ item }}
      </div>
    </div>

  </div>
</template>

<script>
import MathFun from "@/utils/math.js";
export default {
  name: "Home",
  data() {
    return {
      mathArr: [],
      type1: 100,
      type2: 30,
      type3: 30
    };
  },
  components: {},
  methods: {
    make: function () {
      let arr = [];
      arr.push(...this.division());
      this.mathArr = arr;
    },
    division: function (dividendNum = 3, divisorNum = 2, num = 24) {
      let dividend, divisor, formula;
      let arr = [];
      let n = 0;

      while (n < num) {
        dividend = MathFun.getRandom(dividendNum);
        divisor = MathFun.getRandom(divisorNum);

        formula = dividend + '÷' + divisor + "=";

        if (!arr.indexOf(formula) > -1) {
          arr.push(formula);
          n++;
        }
      }

      return arr;
    }
  },
  mounted() {
    this.make();
  }
};
</script>
<style lang="scss">
.home>div {
  display: flex;
  flex-flow: wrap;
  height: 100%;

  >div {
    width: 24.5%;
    text-align: center;
    padding: 9.5px 0;
  }
}
</style>
