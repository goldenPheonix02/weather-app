<template>
<Header/>
  <div class="home">
    <DataCard/>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import Header from "@/components/header.vue";

import DataCard from "@/components/dataCard.vue";

export default {
  name: "Home",
  components: {
    // HelloWorld,
    Header,
    // Input,
    DataCard
  },
};
</script>
