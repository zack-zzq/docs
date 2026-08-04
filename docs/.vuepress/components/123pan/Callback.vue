<script lang="ts" setup>
import { computed, ref } from "vue"
import { NAlert, NInput, NSpace, NSpin } from "naive-ui"
import { api } from "../api"

interface TokenData {
  refresh_token?: string
  refreshToken?: string
}

interface TokenResponse extends TokenData {
  data?: TokenData
  error?: string
  error_description?: string
  message?: string
}

const url = new URL(window.location.href)
const code = url.searchParams.get("code")
const oauthError = url.searchParams.get("error")
const oauthErrorDescription = url.searchParams.get("error_description")

const token = ref<TokenResponse>()
const requestError = ref("")
const loading = ref(false)

const refreshToken = computed(
  () =>
    token.value?.refresh_token ||
    token.value?.refreshToken ||
    token.value?.data?.refresh_token ||
    token.value?.data?.refreshToken ||
    ""
)

const getToken = async () => {
  loading.value = true

  try {
    const resp = await fetch(api("/alist/123pan/code"), {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ code }),
    })
    const res: TokenResponse = await resp.json()

    if (!resp.ok) {
      throw new Error(
        res.error_description || res.error || res.message || `HTTP ${resp.status}`
      )
    }

    token.value = res
    requestError.value = res.error_description || res.error || ""
  } catch (error) {
    requestError.value =
      error instanceof Error ? error.message : String(error)
  } finally {
    loading.value = false
  }
}

if (code && !oauthError) {
  getToken()
}
</script>

<template>
  <NAlert
    v-if="!code || oauthError"
    :title="oauthError || 'Error'"
    type="error"
  >
    {{ oauthErrorDescription || (!code ? "Missing authorization code." : "") }}
  </NAlert>
  <NSpace v-else vertical size="large">
    <NAlert v-if="requestError" title="Error" type="error">
      {{ requestError }}
    </NAlert>
    <NSpace vertical>
      <b>refresh_token:</b>
      <NSpin v-if="loading" />
      <NInput
        v-else-if="refreshToken"
        type="textarea"
        autosize
        readonly
        :value="refreshToken"
      />
      <NAlert v-else-if="token && !requestError" title="Error" type="error">
        The token response does not contain a refresh_token.
      </NAlert>
    </NSpace>
  </NSpace>
</template>
