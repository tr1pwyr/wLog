<template>
  <div class="content">
    <!-- <img :src="theme.avator" width="135" height="135" class="avator" /> -->
  </div>
</template>

<script lang="ts" setup>
import { useData } from "vitepress";
const { theme } = useData();
</script>

<style scoped>
.content {
  display: flex;
  align-items: center;
  justify-content: center;
  /* height: 100px; */
  height: 25px;
}

</style>
