<template>
  <div class="main">
    <h2 class="tags-header">Tags</h2>

    <div class="tagResults">

      <h3 class="header" v-show="selectTag">
        <TagIcon />
        <span class="header-text">{{ selectTag }}</span>
      </h3>

      <a :href="withBase(article.regularPath)" 
        v-for="(article, index) in data[selectTag]" 
        :key="index" class="article">
        <div class="title">
          {{ article.frontMatter.title }}
        </div>
        <div class="date">{{ article.frontMatter.date }}</div>
      </a>

    </div>

    <div class="tags">
      <span @click="toggleTag(key)" 
        v-for="(item, key) in data" 
        class="tag" 
        :style="getFontSize(data[key].length)"
        :class="{ activetag: selectTag === key }">
          {{ key }}
        <span class="tag-length">{{ data[key].length }}</span>
      </span>
    </div>

  </div>

</template>

<script lang="ts" setup>
import { computed, ref } from "vue";
import { useData, withBase } from "vitepress";
import { initTags } from "../utils";
import TagIcon from "./shared/TagIcon.vue";
const { theme } = useData();
const data = computed(() => initTags(theme.value.posts));
let selectTag = ref("");

const toggleTag = (tag: string) => {
  selectTag.value = tag;
};

// length of the list of tags - how many tags are there
const getFontSize = (length: number) => {
  let size = length - .1 * 1.5;
  return { fontSize: `${size}em` };
};

</script>

<style scoped>
.main {
  margin: 0 auto;
  padding: 0.5rem 1.5rem 4rem;
  max-width: 48rem;
}

.tags-header {
  font-weight: bold;
  padding-bottom: 14px;
  font-size: 2em;
  margin-top: 24px;
}

.tags {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: left;
  border-bottom: 1px dashed #c7c7c7;
  margin-bottom: 10px;
  padding-bottom: 20px;
}

.tag {
  display: inline-block;
  margin: 6px 8px;
  font-size: 0.85em;
  line-height: 25px;
  transition: 0.4s;
  color: #a1a1a1;
  cursor: pointer;
}

.tag:hover {
  color: var(--vp-c-hover);
}

.tagResults {
  padding-bottom: 10px;
}

.activetag {
  color: var(--vp-c-hover);
}

.tag-length {
  color: var(--vp-c-brand);
  font-size: 12px !important;
  position: relative;
  top: -8px;
  left: -4px;
}

.header {
  font-size: 1rem;
  font-weight: 600;
  margin: 1.5rem 0;
  display: flex;
  align-items: center;
  justify-content: left;
}

.fas-icon {
  width: 2rem;
  height: 2rem;
}

.header-text {
  padding-left: 10px;
}

.article {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 10px 10px;
  color: var(--vp-c-text-2);
  transition: border 0.3s ease, color 0.3s ease;
}

.article:hover {
  text-decoration: none;
  color: var(--vp-c-brand);
}

.date {
  font-family: Georgia, sans-serif;
}
</style>
