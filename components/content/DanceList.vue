<script setup lang="ts">
const localeStringOptions = computed(() => ({ weekday: 'short', month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit' }))
const dances = await queryContent('dances').find()

const dancesToCome = computed(() => dances.filter(dance => (new Date(dance.startDatetime)).getTime() > (new Date()).getTime()))
</script>

<template>
  <main>
    <div v-for="dance in dancesToCome" :key="dance._path" class="py-5">
      <div class="rounded overflow-hidden shadow-lg border-solid border-2 border-current">
        <img :src="dance.image" class="w-full" alt="Swing Jazz Event">
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">
            <h2 class="my-px py-px">
              {{ dance.name }}
            </h2>
            <p class="inline-block bg-inherit text-indigo-500 border-solid border-2 border-indigo-500 rounded-full px-3 py-1 text-sm mr-2 mb-2">
              {{ new Date(dance.startDatetime).toLocaleString("pt-BR", localeStringOptions) }}
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
  </main>
</template>
