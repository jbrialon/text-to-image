<script>
import Replicate from "../lib/Replicate.js";
const replicate = new Replicate({ proxyUrl: "http://localhost:3000/api" });

const version = "3b5c0242f8925a4ab6c79b4c51e9b4ce6374e9b07b5e8461d89e692fd0faa449";

export default {
  data() {
    return {
      msg: "World",
    };
  },
  async mounted() {
    const helloWorldModel = await replicate.models.get("replicate/hello-world");
    const helloWorldPrediction = await helloWorldModel.predict({ text: this.msg });
    this.msg = helloWorldPrediction;
  },
};
</script>

<template>
  <h1>{{ msg }}</h1>
</template>

<style scoped></style>
