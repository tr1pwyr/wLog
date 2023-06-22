<template>
  <!-- <div>
    <div class="before">heh?</div>
    <div class="after">wha?</div>
  </div> -->

  <!-- <ShareCard /> -->

  <div class="blogList">
    <a class="blog" v-for="item in posts" :href="withBase(item.regularPath)">
      <div class="blogContainer">
        <div class="cover flex-item">
          <img 
            :alt = "item.frontMatter.title"
            :src="item.frontMatter.thumbnail" 
            class="thumbnail" />
        </div>
        <div class="meta flex-item">
          <div class="title">
            {{ item.frontMatter.title }}
          </div>
          <div class="description">
            {{ item.frontMatter.description }}
          </div>
          <div class="date">
            {{ transDate(item.frontMatter.date) }}
          </div>
          <div class="tags">
            <span class="tag" v-for="tag in item.frontMatter.tags">
              {{ tag }} &nbsp;
            </span>
          </div>
        </div>
      </div>
    </a>
  </div>

  <div class="pagination">
    <button class="left" v-if="pageCurrent > 1" @click="go(pageCurrent - 1)">
      Previous page
    </button>
    <div v-if="pagesNum > 1">
      {{ `${pageCurrent}/${pagesNum}` }}
    </div>
    <button class="right" v-if="pageCurrent < pagesNum" @click="go(pageCurrent + 1)">
      Next page
    </button>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
// import ShareCard from "./ShareCard.vue";
import { useData, withBase } from "vitepress";
interface post {
  regularPath: string;
  frontMatter: object;
}

const { theme } = useData();

let postsAll = theme.value.posts || [];
let postLength = theme.value.postLength;
let pageSize = theme.value.pageSize;

let pagesNum =
  postLength % pageSize === 0
    ? postLength / pageSize
    : postLength / pageSize + 1;

pagesNum = parseInt(pagesNum.toString());

let pageCurrent = ref(1);

postsAll = postsAll.filter((item: post) => {
  return item.regularPath.indexOf("index") < 0;
});

let allMap = {};
for (let i = 0; i < pagesNum; i++) {
  allMap[i] = [];
}
let index = 0;
for (let i = 0; i < postsAll.length; i++) {
  if (allMap[index].length > pageSize - 1) {
    index += 1;
  }
  allMap[index].push(postsAll[i]);
}

let posts = ref([]);
posts.value = allMap[pageCurrent.value - 1];

// click pagination
const go = (i) => {
  pageCurrent.value = i;
  posts.value = allMap[pageCurrent.value - 1];
};

const transDate = (date: string) => {
  const dateArray = date.split("-");
  let year = dateArray[0],
    month = ``,
    day = dateArray[2];
  switch (dateArray[1]) {
    case "1":
    case "01":
      month = `Jan`;
      break;
    case "2":
    case "02":
      month = `Feb`;
      break;
    case "3":
    case "03":
      month = `Mar`;
      break;
    case "4":
    case "04":
      month = `Apr`;
      break;
    case "5":
    case "05":
      month = `May`;
      break;
    case "6":
    case "06":
      month = `Jun`;
      break;
    case "7":
    case "07":
      month = `Jul`;
      break;
    case "8":
    case "08":
      month = `Aug`;
      break;
    case "9":
    case "09":
      month = `Sep`;
      break;
    case "10":
      month = `Oct`;
      break;
    case "11":
      month = `Nov`;
      break;
    case "12":
      month = `Dec`;
      break;
    default:
      month = `Month`;
  }
  return `${month} ${day}, ${year}`;
};
</script>

<style scoped>
.blog-title {
  text-align: center;
  font-weight: bold;
  font-size: 2rem;
  margin-top: 24px;
}

.blogList {
  padding: 10px 0 30px 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.blog {
  width: 100%;
  display: block;
  border-radius: 10px;
  padding: 10px;
  margin: 10px 0;
  background: rgb(255, 255, 255, .5);
  border: 1px solid white;
  max-width: 800px;
  /* box-shadow: 6px 6px var(--vp-c-brand); */
  cursor: pointer;
}

.dark .blog {
  background: rgb(39, 39, 39, .25);
  border: 1px solid rgb(39, 39, 39, .25);
}

.blog:hover {
  text-decoration: none;
  background-color: rgb(255, 255, 255, .9);
  transform: translate(-2px, -2px);
  filter: drop-shadow(5px 5px 10px rgb(0, 0, 0, .1));
  border: 1px solid rgb(0, 0, 0, .1);
}

.dark .blog:hover {
  background-color: rgb(0, 0, 0, .33);
  border: 1px solid rgb(256, 256, 256, .2);
}

.title {
  color: var(--vp-c-brand-light);
  font-size: 1em;
  font-weight: 500;
  line-height: 1;
  padding: 0 0 5px 5px;
}

.description {
  font-size: .75em;
  line-height: 1.2;
  color: #777;
  padding-left:5px;
}

.date {
  padding: 1px 0 1px 5px;
  font-size: .7rem;
}

.pagination {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 85%;
  max-width: 600px;
  margin: 0 auto;
  position: relative;
}

.left {
  position: absolute;
  left: 0;
}

.right {
  position: absolute;
  right: 0;
}

.thumbnail {
  width: 100px;
  height: 100px;
  margin-bottom: 5px;
  border-radius: 5px;
  object-fit: cover;
}


.blogContainer {
  display: flex;
  flex-wrap: wrap;
  justify-content: left;
  align-items: left;
  column-gap: 5px;
}

.meta {
  padding-top: 10px;
}

.tags {
  display: flex;
  border-radius: 5px;
  background: #fff;
}

.dark .tags {
  background: rgb(0, 0, 0, .7);
  color: #fff;
} 

.tag{
  display: flex;
  padding-left: .5em;
  margin-right: .3rem;
  color: var(--slate);
  font-size: .75rem;
  font-weight: 500;

}



/* Media query for small screens */
@media screen and (max-width: 767px) {
  .flex-item {
    flex-basis: 100%;
    /* Display one item in a single column */
  }
}
</style>
