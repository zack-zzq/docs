<script setup lang="ts">
import { ref, onMounted } from "vue"

// 全局版本状态，避免重复请求
const globalVersionState = {
  version: ref<string>(""),
  loading: ref<boolean>(true),
  promise: null as Promise<void> | null
}

// 如果还没有请求过，创建一个全局请求
if (!globalVersionState.promise) {
  globalVersionState.promise = (async () => {
    try {
      const res = await fetch("https://dapi.alistgo.com/v0/version/latest")
      const data = await res.json()
      globalVersionState.version.value = data.version
    } catch (err) {
      console.error("fetch version failed", err)
      // 失败时设置默认版本，避免无限等待
      globalVersionState.version.value = "3.52.0"
    } finally {
      globalVersionState.loading.value = false
    }
  })()
}

const version = globalVersionState.version
const loading = globalVersionState.loading

const props = defineProps<{
  // 服务端下载使用：传入文件名后缀，例如 "windows-arm64.zip"
  filename?: string
  // 下载类型：server(默认) 或 desktop
  type?: "server" | "desktop"
  // 桌面版下载使用：完整文件名模板，使用 {ver} 作为版本占位
  // 例如："alist-desktop_{ver}_aarch64.dmg"
  tpl?: string
}>()

onMounted(async () => {
  // 等待全局版本加载完成
  await globalVersionState.promise
})

function buildUrl() {
  const v = version.value
  const type = props.type ?? "server"

  if (type === "desktop") {
    // 桌面版下载地址：
    // https://alistgo.com/download/Alist/desktop-v${version}/${tpl}
    // 例如：alist-desktop_{ver}_aarch64.dmg
    const filenameFromTpl = (props.tpl ?? "alist-desktop_{ver}_aarch64.dmg").replaceAll("{ver}", v)
    return `https://alistgo.com/download/Alist/desktop-v${v}/${filenameFromTpl}`
  }

  // 服务端下载地址：
  // https://alistgo.com/download/Alist/v${version}/alist-${version}-${filename}
  const filename = props.filename ?? ""
  return `https://alistgo.com/download/Alist/v${v}/alist-${v}-${filename}`
}

// i18n: 按路径判断中英文
let downText = "Download"
if (location.pathname.startsWith("/zh/")) {
  downText = "下载"
}
</script>

<template>
  <span v-if="loading" class="loading">{{ downText }}...</span>
  <a v-else :href="buildUrl()" target="_blank">{{ downText }}</a>
</template>

<style scoped>
a {
  color: var(--vp-c-brand);
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

.loading {
  color: var(--vp-c-text-3);
  opacity: 0.7;
}
</style>
