<template>
  <div class="d-flex">
    <div
      class="p-3 rounded"
      style="max-width: 400px; margin: 50px auto; background: #234"
    >
      <div
        class="w-full rounded m-1 p-3 text-end lead font-weight-bold text-white bg-vue-dark"
      >
        {{ output || 0 }}
      </div>
      <div class="row no-gutters">
        <div class="col-3" v-for="n in input" :key="n">
          <div
            class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
            :class="{
              'bg-vue-green': ['C', '*', '-', '+', '/', '%', '='].includes(n),
            }"
            @click="calculate(n)"
          >
            {{ n }}
          </div>
        </div>
      </div>
    </div>
    <div
      class="p-5 m-4 rounded"
      style="
        max-width: 300px;
        max-height: 300px;
        margin: 20px auto;
        background: #234;
      "
    >
      <div class="m-1 p-4 text-white font-weight-bold bg-vue-dark">
        {{ count }}
      </div>
      <div class="row-2 no-gutters">
        <div class="col-2" v-for="b in btns" :key="b">
          <div
            class="btn btn-primary lead text-white text-center m-1 py-2 hover-class"
            @click="counter(b)"
          >
            {{ b }}
          </div>
        </div>
      </div>
    </div>
    <div class="search-box p-5 m-">
      <div>
        <input type="text" placeholder="search" v-model="search" />
      </div>
      <div class="m-2 text-start" v-for="(user, i) in usersList" :key="i">
        <strong> {{ i + 1 }}.</strong> {{ user.name }}
      </div>
    </div>
  </div>

  <!-- <div class="calculator">
      <input type="text" placeholder="0" id="inputBox" />
      <div class="btsp">

      </div>
      <div>
        <button class="operator">AC</button>
        <button class="operator">Del</button>
        <button class="operator">%</button>
        <button class="operator">/</button>
      </div>
      <div>
        <button>7</button>
        <button>8</button>
        <button>9</button>
        <button class="operator">+</button>
      </div>
      <div>
        <button>4</button>
        <button>5</button>
        <button>6</button>
        <button class="operator">*</button>
      </div>
      <div>
        <button>1</button>
        <button>2</button>
        <button>3</button>
        <button class="operator">-</button>
      </div>
      <div>
        <button>00</button>
        <button>0</button>
        <button class="operator">.</button>
        <button class="eq">=</button>
      </div>
    </div> -->
</template>

<script>
export default {
  name: "HelloWorld",

  data() {
    return {
      msg: "Calculator",
      output: "",
      input: [
        "C",
        "*",
        "/",
        "-",
        "7",
        "8",
        "9",
        "+",
        "4",
        "5",
        "6",
        "%",
        "1",
        "2",
        "3",
        "=",
        "0",
        ".",
        "Del",
      ],
      count: 0,
      btns: ["increase", "decrease", "reset"],
      operator: null,
      previousValue: "",
      users: [
        {
          name: "penny",
        },
        {
          name: "leonard",
        },
        {
          name: "sheldon",
        },
        {
          name: "raj",
        },
      ],
      search: "",
    };
  },
  computed: {
    usersList() {
      if (this.search.trim().length>0) {
        return this.users.filter((u)=>u.name.includes(this.search.trim()))
      }
      return this.users;
    },
  },
  methods: {
    calculate(n) {
      // let input=document.getElementById('inputBox')
      // let buttons = document.querySelectorAll('button')
      if (!isNaN(n) || n === ".") {
        this.output += n + "";
      }
      if (n === "C") {
        this.output = "";
      }
      if (["C", "*", "-", "+", "/", "%"].includes(n)) {
        this.operator = n;
        this.previousValue = this.output;
        this.output = this.previousValue + this.operator;
      }
      if (n === "=") {
        this.output = eval(this.previousValue + this.operator + this.output);
        this.previousValue = "";
        this.operator = null;
      }
      if (n === "Del") {
        this.output = this.output.substring(0, this.output.length - 1);
      }
    },
    counter(b) {
      if (b == "increase") {
        this.count++;
      }
      if (b == "decrease") {
        this.count--;
      }
      if (b == "reset") {
        this.count = 0;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
/* @media screen and (min-width: 768px) {
  *{
    height: 100vh;
    justify-content: center;
    align-items: center;
  }
} */
.bg-vue-dark {
  background: #31475e;
}
.bg-vue-green {
  background: #6ef7be;
}
.hover-class:hover {
  cursor: pointer;
  background: #3d5875;
}
.search-box{
  width: 500px;
  height: 500px;
  background: white;
  margin: 20px auto;

}
.names{
 margin: top 10px; 
  align-items: ends;
  position: relative;
}
/* .calculator {
  border: 1px solid black;
  padding: 20px;
  font-family: "Courier New", Courier, monospace;
  border-radius: 20px;
  background-color: transparent; 
}
input{
  width: 320px;
  border:none;
  font-size: medium;
  box-shadow: 0px 3px 15px rgba(112, 103, 103, 0.5);
 background: transparent;
 cursor: pointer;
 margin: 10px;
 padding: 10px;
}
input::placeholder{
  text-align: right;
  color: aqua;
}
button{
  border: none;
  width: 60px;
  height: 60px;
  border-radius: 40px;
  margin: 10px;
  background: transparent;
  color: aliceblue;
  font-size: medium;
  box-shadow: -8px -8px 15px rgba(255, 255, 255, 0.1);
}
.operator{
  color: black;
  background-color: paleturquoise;
}
.eq{
  color: azure;
  background: black;
} */
</style>

