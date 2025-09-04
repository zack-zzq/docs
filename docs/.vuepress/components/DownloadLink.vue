<script setup lang="ts">
import { inject } from "vue"

const VERSION_KEY = "alist-version"
const VERSION_LOADING_KEY = "alist-version-loading"

// 从Provider获取全局状态
const version = inject<ReturnType<typeof ref<string>>>(VERSION_KEY)
const loading = inject<ReturnType<typeof ref<boolean>>>(VERSION_LOADING_KEY)

if (!version || !loading) {
  throw new Error("DownloadLink must be used within VersionProvider")
}

const props = defineProps<{
  // 服务端下载使用：传入文件名后缀，例如 "windows-arm64.zip"
  filename?: string
  // 下载类型：server(默认) 或 desktop
  type?: "server" | "desktop"
  // 桌面版下载使用：完整文件名模板，使用 {ver} 作为版本占位
  // 例如："alist-desktop_{ver}_aarch64.dmg"
  tpl?: string
}>()

// 不再需要onMounted钩子，因为我们在组件初始化时就处理了版本获取

function buildUrl() {
  const v = version.value
  const type = props.type ?? "server"

  if (type === "desktop") {
    // 桌面版下载地址：
    // https://alistgo.com/download/Alist/desktop-v${version}/${tpl}
    // 例如：alist-desktop_{ver}_aarch64.dmg
    const filenameFromTpl = (props.tpl ?? "alist-desktop_{ver}_aarch64.dmg").replaceAll("{ver}", v || "3.52.0")
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
