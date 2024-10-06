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
      // arr.push(...this.addAndReduce(this.type1, 101));
      arr.push(...this.add(40, 101));
      arr.push(...this.add(40, 1001));
      arr.push(...this.multiplication(40, 101, 10));
      // arr.push(...this.wholeTenMultiplication(40));
      arr = this.shuffleSelf(arr, 100);
      this.mathArr = arr;
    },
    addAndReduce: function (num, limit = 21) {
      let n = 0;
      let arr = [];
      let x;
      let a, b, c;
      let z, z1;
      while (n < num) {
        x = Math.floor(Math.random() * 2);
        a = Math.floor(Math.random() * limit);
        if (x == 0) {
          b = Math.floor(Math.random() * (limit - a));
          z = a + "+" + b;
          z1 = a * 1 + b * 1;
        } else {
          b = Math.floor(Math.random() * a);
          z = a + "-" + b;
          z1 = a * 1 - b * 1;
        }
        if (a < 6 && b < 6) {
          continue;
        }
        c = Math.floor(Math.random() * Math.floor(limit / 2));
        if (z1 > Math.floor(limit / 2)) {
          z += "-" + c + "=";
        } else {
          z += "+" + c + "=";
        }
        if (!arr.indexOf(z) > -1) {
          arr.push(z);
          n++;
        }
      }
      return arr;
    },
    add: function (num, limit = 21) {
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
        if (a < 10 || b < 10) {
          continue;
        }
        if (!arr.indexOf(z) > -1) {
          arr.push(z);
          n++;
        }
      }
      return arr;
    },
    multiplication: function (num, limita = 101, limitb = 10) {
      let n = 0;
      let arr = [];
      let a;
      let b;
      let z;
      while (n < num) {
        a = Math.floor(Math.random() * limita);
        b = Math.floor(Math.random() * limitb);
        z = a + "x" + b + "=";
        if (a <= 10 || b < 2) {
          continue;
        }
        if (!arr.indexOf(z) > -1) {
          arr.push(z);
          n++;
        }
      }
      return arr;
    },
    wholeTenMultiplication: function (num) {
      let n = 0;
      let x, a, b, z;
      let arr = [];
      while (n < num) {
        x = Math.floor(Math.random() * 2) + 1;
        a = Math.floor(Math.random() * 9) + 1;
        a = a * Math.pow(10, x);
        b = Math.floor(Math.random() * 6) + 4;
        z = a + "x" + b + "=";
        if (!arr.indexOf(z) > -1) {
          arr.push(z);
          n++;
        }
      }
      return arr;
    },
    wholeTenAddWholeTen: function (num) {
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
    },
    shuffleSelf: function (array, size) {
      let index = -1;
      let length = array.length;
      let lastIndex = length - 1;
      let value;

      size = size === undefined ? length : size;
      while (++index < size) {
        // var rand = baseRandom(index, lastIndex),
        var rand = index + Math.floor(Math.random() * (lastIndex - index + 1));
        value = array[rand];

        array[rand] = array[index];

        array[index] = value;
      }
      array.length = size;
      return array;
    }
  },
  mounted() {
    this.make();
  }
};
</script>
<style lang="scss">
html,
body,
#app,
.home {
  height: 99%;
}

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
