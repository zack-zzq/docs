<script lang="ts" setup>
import { NAlert, NButton, NSpace } from "naive-ui"

const authUrl =
  "https://yun.123pan.com/auth?client_id=zpcup2ci1kmy62s8mkbc363e32z2v9l5&redirect_uri=https%3A%2F%2Falistgo.com%2Ftool%2F123pan%2Fcallback&scope=user:base,file:all:read,file:all:write&state=alist"

const goGet = () => {
  window.open(authUrl, "_blank", "noopener,noreferrer")
}
</script>

<template>
  <NSpace vertical size="large">
    <NAlert title="123Pan Open" type="info">
      使用 123Pan 官方第三方授权应用获取刷新 Token，无需申请个人开发者。
    </NAlert>
    <NButton size="large" type="primary" block @click="goGet">
      获取刷新 Token
    </NButton>
  </NSpace>
</template>
