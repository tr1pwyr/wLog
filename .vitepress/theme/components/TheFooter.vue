<template>
  <footer>
    [wL] v.0.0.2 by <a href="https://tr1pwyr.com" target="_blank" title="Tr1pwyr">
      Tr1pwyr
    </a >Copyright &copy; {{ date }}
  </footer>
</template>
<script lang="ts" setup>
const date = new Date().getFullYear();
</script>
<style scoped>
footer {
  display: block;
  text-align: center;
  position: absolute;
  width: 100%;
  bottom: 20px;
  padding: 0 20px;
  background-color: var(--vp-c-bg);
  color: var(--vp-c-text);
}
a {
  color: var(--vp-c-brand);
  font-weight: bold;
}
a:hover {
  text-decoration: none;
  color: var(--vp-c-hover);
}
</style>
