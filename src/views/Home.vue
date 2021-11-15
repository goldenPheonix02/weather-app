<template>
  <Header />
  <div class="home">
    <DataCard />
  </div>
  <Footer />
</template>

<script>
// @ is an alias to /src

import Header from "@/components/header.vue";
import Footer from "@/components/footer.vue";
import DataCard from "@/components/dataCard.vue";

export default {
  name: "Home",
  components: {
    // HelloWorld,
    Header,
    Footer,
    // Input,
    DataCard,
  },
};
</script>
