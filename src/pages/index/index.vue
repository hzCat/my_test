<template>
  <div class="container">
    <label for="name">name:</label><input class="name" type="text" v-model="user_name">
    <label for="password">password:</label><input class="password" type="password" v-model="user_pwd">
    <button @click="submit">submit</button>
    <div>
      <div><a href="javascript:void(0)" @click="goAnchor('#anchor-'+index)" v-for="index in 20" :key="index"> {{index}} </a></div>
      <div :id="'anchor-'+index" class="item" v-for="index in 20" :key="index">{{index}}</div>
    </div>
  </div>
</template>

<script>
export default {
  date() {
    return {
      user_name: "",
      user_pwd: ""
    };
  },
  methods: {
    submit() {
      let name = this.user_name;
      let pwd = this.user_pwd;
      var data = {
        name: name,
        pwd: pwd
      };
      console.log(data);
      this.ajax.post("/test/login", data).then(res => {
        console.log(res);
      });
    },
    goAnchor(selector) {
      var anchor = this.$el.querySelector(selector);
      document.documentElement.scrollTop = anchor.offsetTop;
    }
  }
};
</script>

<style>
.item {
  line-height: 100px;
}
</style>
