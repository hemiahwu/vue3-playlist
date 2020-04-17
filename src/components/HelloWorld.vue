<template>
  <div class="hello">
    <h1>腾讯课堂: {{ state.name }} 微信: {{ state.wechat }}</h1>
    <div v-for="(user, index) in state.users" :key="index">
      <p>{{ user.name }}</p>
      <p>{{ user.email }}</p>
    </div>
    <button @click="fetchData()">获取数据</button>
    <div v-for="(user, index) in state.users" :key="index">
      <p>{{ user.name }}</p>
      <p>{{ user.email }}</p>
    </div>
  </div>
</template>

<script>
import { reactive, computed, onMounted } from "vue";
import axios from "axios";
export default {
  setup() {
    const state = reactive({
      name: "米修在线",
      wechat: "27732357",
      users: [],
    });

    // onMounted(() => {
    //   fetchData();
    // });

    function fetchData() {
      axios.get("http://jsonplaceholder.typicode.com/users").then((res) => {
        // console.log(res.data);
        state.users = res.data;
      });
    }

    return { state, fetchData };
  },
};
</script>
