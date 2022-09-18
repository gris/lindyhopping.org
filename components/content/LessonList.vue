<script setup lang="ts">
import { ref } from 'vue'
const localeStringOptions = computed(() => ({ weekday: 'short', month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit' }))
const lessons = await queryContent('lessons').find()
const shouldShowPastLessons = ref(false)

const lessonsToShow = computed(() => lessons.filter(lesson => shouldShowPastLessons.value ? (new Date(lesson.startDatetime)).getTime() < (new Date()).getTime() : (new Date(lesson.startDatetime)).getTime() > (new Date()).getTime()))
lessonsToShow.value.sort((a, b) => (new Date(a.startDatetime)).getTime() - (new Date(b.startDatetime)).getTime())

function toggleShouldShowPastLessons () {
  shouldShowPastLessons.value = !shouldShowPastLessons.value
  if (shouldShowPastLessons.value) {
    lessonsToShow.value.sort((a, b) => (new Date(b.startDatetime)).getTime() - (new Date(a.startDatetime)).getTime())
  } else {
    lessonsToShow.value.sort((a, b) => (new Date(a.startDatetime)).getTime() - (new Date(b.startDatetime)).getTime())
  }
}

</script>

<template>
  <main>
    <button class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded" @click="toggleShouldShowPastLessons">
      {{ shouldShowPastLessons ? 'Próximas Aulas' : 'Aulas Passadas' }}
    </button>
    <div v-for="lesson in lessonsToShow" :key="lesson._path" class="py-5">
      <div class="rounded overflow-hidden shadow-lg border-solid border-2 border-current">
        <img :src="lesson.image" class="w-full" alt="Swing Jazz Event">
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">
            <h2 class="my-px py-px">
              {{ lesson.name }}
            </h2>
            <p class="inline-block bg-inherit text-indigo-500 border-solid border-2 border-indigo-500 rounded-full px-3 py-1 text-sm mr-2 mb-2">
              {{ new Date(lesson.startDatetime).toLocaleString("pt-BR", localeStringOptions) }}
            </p>
          </div>
          <p><Icon name="noto:woman-dancing-light-skin-tone" class=".text-indigo-400 .w-5 .h-5" /> Professora: {{ lesson.teacher }}</p>
          <p>{{ lesson.description }}</p>
          <div v-if="lesson.playlist">
            <p>
              Playlist da aula: <NuxtLink
                :key="lesson.playlist"
                :to="lesson.playlist"
              >
                <Icon
                  name="logos:spotify-icon"
                />
              </NuxtLink>
            </p>
          </div>
          <p><Icon name="noto:backhand-index-pointing-right" class=".text-indigo-400 .w-5 .h-5" /> Endereço: {{ lesson.address }}</p>
          <p><Icon name="fluent-emoji:money-bag" class=".text-indigo-400 .w-5 .h-5" /> {{ lesson.price }}</p>
        </div>
      </div>
    </div>
  </main>
</template>
