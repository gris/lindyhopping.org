<template>
  <div class="sm:pt-6 sm:pb-10">
    <Html lang="pt-br" />
    <Meta property="og:image" content="/lindy-hop-couple.png" />
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
