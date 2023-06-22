<template>
  <Layout>
    <template #doc-before>
      <Title />
      <!-- <Category /> -->
    </template>

    <template #doc-after>
      <button @click="back">Back</button>
      <Comments />
    </template>

    <!-- <template #home-hero-before><HomeHero /> </template> -->
    <template #home-features-after>
      <Page />
    </template>

  </Layout>
  <Footer />
</template>

<script lang="ts" setup>
import DefaultTheme from "vitepress/theme";
// import HomeHero from "./HomeHero.vue";
import Footer from "./TheFooter.vue";
import Comments from "./Comments.vue";
import Page from "./Page.vue";
// import Category from "./Category.vue";
import Title from "./Title.vue";
const { Layout } = DefaultTheme;
const back = () => {
  history.back();
};
</script>
