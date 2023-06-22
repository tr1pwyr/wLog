<template>
  <div v-for="yearList in data" class="yearItem main">
    <div class="year">
      {{ yearList[0].frontMatter.date.split("-")[0] }}
    </div>
    <a :href="withBase(article.regularPath)" 
      v-for="(article, index) in yearList" 
      :key="index" class="article">
      <div class="title">
        {{ article.frontMatter.title }}
      </div>
      <div>{{ article.frontMatter.date.slice(5) }}</div>
    </a>
  </div>
</template>

<script lang="ts" setup>
import { useData, withBase } from "vitepress";
import { computed } from "vue";
import { useYearSort } from "../utils";
const { theme } = useData();
const data = computed(() => useYearSort(theme.value.posts));
</script>

<style scoped>
.main {
  margin: 2rem auto;
  padding: 0.5rem 0.5rem 4rem 0.5rem;
  max-width: 64rem;
}

.yearItem {
  border-bottom: 1px dashed #c7c7c7;
  padding-bottom: 1rem;
}

.dark .yearItem {
  border-bottom: 1px dashed #313131;
}

.yearItem:last-child {
  border: none;
}

.year {
  padding: 12px 0 8px 8px;
  font-size: 1.2rem;
  font-weight: 800;
  background-color: rgb(255, 255, 255, .5);
}

.dark .year {
  background-color: rgb(0, 0, 0, .5);
}

.article {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 5px;
  padding: 5px;
  color: var(--vp-c-text-2);
  transition: border 0.3s ease, color 0.3s ease;
  border-radius: .2rem;
  font-weight: 600;
  border-bottom: 2px solid transparent;
}

.article:hover {
  text-decoration: none;
  color: black;
  background-color: rgb(255, 255, 255, .5);
  border-bottom: 3px solid var(--vp-c-brand-dark);
}

.dark .article:hover {
  text-decoration: none;
  color: white;
  background-color: rgb(0, 0, 0, .5);
  border-bottom: 3px solid var(--vp-c-brand-dark);
}

</style>
