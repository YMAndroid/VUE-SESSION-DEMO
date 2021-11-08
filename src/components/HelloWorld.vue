<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <label>{{ chooseValue }}</label>
    <router-link :to="{ name: 'HelloWorldTwo' }">jump </router-link>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Hello World One",
      chooseValue: "",
    };
  },
  mounted() {
    window.addEventListener("setItem", this.printLog);
  },
  //页面销毁
  beforeDestroy() {
    window.removeEventListener("setItem", this.printLog);
  },
  methods: {
    printLog() {
      console.log("监听到数据变化");
      this.chooseValue = sessionStorage.getItem("menuItem");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
