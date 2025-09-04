<script setup lang="ts">
import { ref, provide } from "vue"

const VERSION_KEY = "alist-version"
const VERSION_LOADING_KEY = "alist-version-loading"

// 创建全局状态
const version = ref("")
const loading = ref(true)

// 提供给子组件使用
provide(VERSION_KEY, version)
provide(VERSION_LOADING_KEY, loading)

// 只在根组件初始化时获取一次版本
fetch("https://dapi.alistgo.com/v0/version/latest")
  .then(res => res.json())
  .then(data => {
    version.value = data.version
  })
  .catch(err => {
    console.error("fetch version failed", err)
    version.value = "3.52.0"
  })
  .finally(() => {
    loading.value = false
  })
</script>

<template>
  <slot></slot>
</template>
