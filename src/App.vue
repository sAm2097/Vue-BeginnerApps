<template>
  <div>
    <h1 class="font-weight-bold text-white m-5">Calculator</h1>

<the-calculator></the-calculator>
  </div>
</template>

<script>
 import TheCalculator from './components/TheCalculator.vue'

export default {
  name: "App",
  components: {
    TheCalculator
  },
  data() {
    return {
      bgColors: ["Red", "black", "yellow"],
      bgColor: "",
    };
  },
  methods: {
    // changeColor() {
    //   console.log("Change");
    //   this.bgColor =
    //     this.bgColors[Math.floor(Math.random() * this.bgColors.length)];
    //   let cont = document.getElementsByClassName("container")[0];
    //   cont.style.background = this.bgColor;
    // },
  },
};
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  box-sizing: border-box;
  margin: 0;
  padding: 0;  
  display: flex;
  justify-content: center;
  background: linear-gradient(45deg,#12162c,#4e6789);
  width: 100%;
  height: 100%;
}


</style>
