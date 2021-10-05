<template>
    <div>
      <Header/>
      <div class="container p-2">
        <router-view />
      </div>
    </div>     
</template>

<script>
import Header from "@/components/Header";

export default {
  components: {
    Header,
  },
};
</script>

<style scoped>
 
</style>