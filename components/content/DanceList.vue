<script setup lang="ts">
const localeStringOptions = computed(() => ({ weekday: 'short', month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit' }))
</script>

<template>
  <main>
    <ContentList v-slot="{ list }" path="/dances">
      <div v-for="dance in list" :key="dance._path" class="py-5">
        <div v-if="new Date(dance.startDatetime) < new Date()" class="rounded overflow-hidden shadow-lg border-solid border-2 border-current">
          <img :src="dance.image" class="w-full" alt="Swing Jazz Event">
          <div class="px-6 py-4">
            <div class="font-bold text-xl mb-2">
              <h2 class="my-px py-px">
                {{ dance.name }}
              </h2>
              <p class="inline-block bg-inherit text-indigo-500 border-solid border-2 border-indigo-500 rounded-full px-3 py-1 text-sm mr-2 mb-2">
                {{ dance.startDatetime.toLocaleString("pt-BR", localeStringOptions) }}
              </p>
            </div>
            <p>{{ dance.description }}</p>
            <div v-if="dance.playlist">
              <p>
                Playlist do baile: <NuxtLink
                  :key="dance.playlist"
                  :to="dance.playlist"
                >
                  <Icon
                    name="logos:spotify-icon"
                  />
                </NuxtLink>
              </p>
            </div>
            <p><Icon name="noto:backhand-index-pointing-right" class=".text-indigo-400 .w-5 .h-5" /> Endereço: {{ dance.address }}</p>
            <p><Icon name="fluent-emoji:money-bag" class=".text-indigo-400 .w-5 .h-5" /> {{ dance.price }}</p>
          </div>
        </div>
      </div>
    </ContentList>
  </main>
</template>
