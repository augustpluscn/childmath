<template>
  <div class="home">
    <div>
      <div v-for="(item,index) in mathArr" :key="index">
        {{item}}
      </div>
    </div>

  </div>
</template>

<script>
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
    make: function() {
      let arr = [];
      arr.push(...this.add(this.type1, 101));
      // arr.push(...this.wholeTenAddSingle(this.type2));
      // arr.push(...this.wholeTenAddWholeTen(this.type3));
      console.log(arr);
      this.mathArr = arr;
    },
    add: function(num, limit = 21) {
      let n = 0;
      let arr = [];
      let x;
      let a;
      let b;
      let z;
      while (n < num) {
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
      return arr;
    },
    wholeTenAddSingle: function(num) {
      let n = 0;
      let x, a, b, z;
      let arr = [];
      while (n < num) {
        x = Math.floor(Math.random() * 2);
        a = Math.floor(Math.random() * 9) + 1;
        b = Math.floor(Math.random() * 9) + 1;
        if (x == 0) {
          z = a * 10 + "+" + b + "=";
        } else {
          z = a * 10 + "-" + b + "=";
        }
        if (!arr.indexOf(z) > -1) {
          arr.push(z);
          n++;
        }
      }
      return arr;
    },
    wholeTenAddWholeTen: function(num) {
      let n = 0;
      let arr = [];
      let x;
      let a;
      let b;
      let z;
      while (n < num) {
        x = Math.floor(Math.random() * 2);
        a = Math.floor(Math.random() * 11);
        if (x == 0) {
          b = Math.floor(Math.random() * (11 - a));
          z = a * 10 + "+" + b * 10 + "=";
        } else {
          b = Math.floor(Math.random() * a);
          z = a * 10 + "-" + b * 10 + "=";
        }
        if (a < 3 || b < 1) {
          continue;
        }
        if (!arr.indexOf(z) > -1) {
          arr.push(z);
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
.home > div {
  display: flex;
  flex-flow: wrap;
  height: 100%;
  > div {
    width: 24.5%;
    text-align: center;
    padding: 9.5px 0;
  }
}
</style>
