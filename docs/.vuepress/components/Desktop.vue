<script setup lang="ts">
import { NButtonGroup, NImage, NSpace, NButton, NDropdown, NTooltip, NPopover } from "naive-ui"
import { computed, ref } from "vue"
// import { api } from "./api";

const proxy = "https://ghfast.top/"
let version: string | undefined

try {
  const res = await fetch(`https://dapi.alistgo.com/v0/version/latest`)
  if (res.ok) {
    const data = await res.json()
    version = data.version as string
  }
} catch (error) {
  console.warn('Failed to fetch version:', error)
  // 如果获取版本失败，不影响组件正常渲染
}

const raw = [
  {
    key: "mac_arm64",
    label: "MacOS (Apple Silicon)",
    url: `https://alistgo.com/download/Alist/desktop-v${version}/alist-desktop_${version}_aarch64.dmg`,
  },
  {
    key: "mac_x64",
    label: "MacOS (Intel)",
    url: `https://alistgo.com/download/Alist/desktop-v${version}/alist-desktop_${version}_x64.dmg`,
  },
  {
    key: "win_x64",
    label: "Windows (X64)",
    url: `https://alistgo.com/download/Alist/desktop-v${version}/alist-desktop_${version}_x64-setup.exe`,
  },
  {
    key: "win_arm64",
    label: "Windows (ARM64)",
    url: `https://alistgo.com/download/Alist/desktop-v${version}/alist-desktop_${version}_arm64-setup.exe`,
  },
  {
    key: "linux",
    label: "Linux",
    url: `https://alistgo.com/download/Alist/desktop-v${version}/alist-desktop_${version}_amd64.deb`,
  },
] as const

type Plat = (typeof raw)[number]["key"]

const platform = navigator.platform.toLowerCase()
const plat = ref<Plat>("win_x64")
if (platform.includes("win")) {
  plat.value = "win_x64"
} else if (platform.includes("linux")) {
  plat.value = "linux"
} else if (platform.includes("mac")) {
  plat.value = "mac_arm64"
}

console.log(plat.value)

let text = {
  down: "Download",
  website: "Website",
  service: "Contact customer service if you have any questions",
  qrTip: "Scan QR code to contact customer service"
}

const fullPlat = computed(() => {
  return raw.find((item) => item.key === plat.value)?.label
})

const options = computed(() => {
  return raw.map((item) => {
    return {
      ...item,
      label: `${item.label} ${plat.value === item.key ? "✅" : ""}`,
    }
  })
})

if (location.pathname.startsWith("/zh/")) {
  text = {
    down: "下载",
    website: "官网",
    service: "如有问题联系小客服",
    qrTip: "扫码联系客服"
  }
}

function down() {
  const href = raw.find((item) => item.key === plat.value)?.url
  window.open(`${href}`, "_blank")
}

function handleSelect(key) {
  plat.value = key
}

function openWebsite() {
  window.open("https://desktop.alistgo.com/zh", "_blank")
}
</script>

<template>
  <NSpace align="center" vertical size="large">
    <NSpace class="btn">
      <NButton size="large" type="info" @click="openWebsite" tertiary>{{
        text.website
      }}</NButton>
      <NButtonGroup>
        <NDropdown
          trigger="hover"
          :options="options"
          @select="handleSelect"
          size="large"
        >
          <NButton size="large" type="primary" tertiary
            >💻{{ fullPlat }}</NButton
          >
        </NDropdown>
        <NButton size="large" @click="down" type="info" secondary>{{
          text.down
        }}</NButton>
      </NButtonGroup></NSpace
    >
    
    <NImage src="/img/guide/desktop.png"></NImage>
    
    <div class="customer-service">
      <NPopover trigger="hover" placement="top">
        <template #trigger>
          <span class="service-link">{{ text.service }}</span>
        </template>
        <template #default>
          <div class="qr-code-container">
            <img 
              src="https://oss.hutool.cn/000000-hutool/upload/alist/qi%20ye.jpg" 
              :alt="text.qrTip" 
              class="qr-code"
            />
            <p class="qr-tip">{{ text.qrTip }}</p>
          </div>
        </template>
      </NPopover>
    </div>
  </NSpace>
</template>

<style scoped>
.btn {
  transform: scale(125%);
  margin-top: 30px;
  margin-bottom: 30px;
}

.customer-service {
  margin-top: 20px;
  text-align: center;
}

.service-link {
  color: #1890ff;
  text-decoration: underline;
  cursor: pointer;
  font-size: 22px;
  transition: color 0.3s;
}

.service-link:hover {
  color: #40a9ff;
}

.qr-code-container {
  text-align: center;
  padding: 16px;
}

.qr-code {
  width: 250px;
  height: 250px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.qr-tip {
  margin-top: 8px;
  color: gray;
  font-size: 18px;
}
</style>
