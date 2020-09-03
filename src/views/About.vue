<template>
<div class="about">
  <h1>This is an about page</h1>
  <div v-for="item in list" :key="item.id">
    <div>
      <div>{{ item.title }}</div>
      <div>{{ item.description }}</div>
    </div>
  </div>
</div>
</template>

<script>
/* eslint-disable space-before-function-paren */
export default {
  name: "about",
  data() {
    return {
      list: [],
    };
  },
  created() {
    this.$axios.get("/api/tasks").then((response) => {
      const {
        status,
        data
      } = response;
      if (status === 200) {
        this.list = data.tasks;
      }
    });
  },
  mounted() {},
  methods: {},
};
</script>
