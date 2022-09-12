<template>
  <main>
    <ContentList v-slot="{ list }" path="/events">
      <div v-for="event in list" :key="event._path" class="py-5">
        <div class="rounded overflow-hidden shadow-lg border-solid border-2 border-current">
          <img :src="event.image" class="w-full" alt="Swing Jazz Event">
          <div class="px-6 py-4">
            <div class="font-bold text-xl mb-2">
              <h2 class="my-px py-px">
                {{ event.name }}
              </h2>
              <p class="inline-block bg-inherit text-indigo-500 border-solid border-2 border-indigo-500 rounded-full px-3 py-1 text-sm mr-2 mb-2">
                {{ event.date }}
              </p>
            </div>
            <p>{{ event.description }}</p>
            <p><Icon name="noto:backhand-index-pointing-right" class=".text-indigo-400 .w-5 .h-5" /> Endereço: {{ event.address }}</p>
            <p><Icon name="fluent-emoji:money-bag" class=".text-indigo-400 .w-5 .h-5" /> Entrada: {{ event.price }}</p>
          </div>
        </div>
      </div>
    </ContentList>
  </main>
</template>
