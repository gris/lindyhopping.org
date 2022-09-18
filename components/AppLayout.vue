<script setup lang="ts">
useHead({
  script: [
    { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
  ]
})
</script>

<template>
  <div class="sm:pt-6 sm:pb-10">
    <Html lang="pt-br" />
    <Meta property="og:image" content="/img/lindy-hop-couple.png" />
    <AppLoadingBar />
    <AppNavbar />
    <slot />
    <AppFooter />
  </div>
</template>

<style lang="postcss">
body {
  @apply bg-primary-50 dark:bg-primary-900;
}
</style>
