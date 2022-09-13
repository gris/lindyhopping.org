<script lang="ts" setup>
import { computed } from 'vue'

const { navigation } = useContent()
const nav = computed(() => {
  return navigation.value.filter((item: {children?: Array<Object>}) => item.children === undefined)
})

</script>

<template>
  <div class="flex justify-between max-w-2xl px-4 py-4 mx-auto sm:px-8">
    <!-- Social icons & Color Mode -->

    <div class="text-primary-700 dark:text-primary-200">
      <NuxtLink
        v-for="link of nav"
        :key="link._path"
        :to="link._path"
        active-class="font-bold"
        class="mr-6"
      >
        {{ link.title }}
      </NuxtLink>
    </div>

    <div class="space-x-3 transition text-primary-500">
      <ColorModeSwitch class="dark:text-primary-100 hover:text-primary-700 dark:hover:text-primary-300" />
    </div>
  </div>
</template>
