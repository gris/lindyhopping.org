<script lang="ts" setup>
const appConfig = useAppConfig()
</script>

<template>
  <div class="flex justify-between max-w-2xl px-4 py-4 mx-auto sm:px-8">
    <!-- Social icons & Color Mode -->
    <div class="space-x-3 transition text-primary-500">
      <p>Built with <Icon name="noto:heart-suit" /> in Rio <Icon name="nimbus:christ" /></p>
    </div>
    <div class="space-x-3 transition text-primary-500">
      <a v-if="appConfig.socials?.github" :href="`https://github.com/${appConfig.socials?.github}`" title="GitHub" class="dark:text-primary-100 hover:text-primary-700 dark:hover:text-primary-300"><Icon name="fa-brands:github" class="w-5 h-5" /></a>
    </div>
  </div>
</template>
