<template>
  <div>
    <h1>{{ msg }}</h1>
    <h2>{{ remotemsg }}</h2>
  </div>
</template>

<script>
const https = require("http");
export default {
  name: "4DComponent",
  props: {
    msg: String,
    remotemsg: String,
  },
  methods: {
    getRemoteMsg() {
      var url = window.location.href + "hello";
      https.get(url, (res) => {
        res.on("data", (data) => {
          this.remotemsg = data;
        });
      });
    },
  },
  created() {
    this.getRemoteMsg();
  },
};
</script>
