<template>
  <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-6">
    <div class="flex flex-col gap-4 lg:flex-row lg:items-center lg:justify-between mb-6">
      <div>
        <p class="text-zinc-500 text-sm">Visualização</p>
        <h2 class="text-2xl font-semibold mt-1">Calendário de hábitos</h2>
      </div>
      <div class="flex gap-2 flex-wrap">
        <button class="bg-white text-black px-4 py-2 rounded-xl text-sm font-medium">Dia</button>
        <button class="bg-zinc-950 border border-zinc-800 px-4 py-2 rounded-xl text-sm">Semana</button>
        <button class="bg-zinc-950 border border-zinc-800 px-4 py-2 rounded-xl text-sm">Mês</button>
      </div>
    </div>

    <div class="space-y-3 overflow-x-auto pb-2">
      <div
        v-for="(habit, index) in habits"
        :key="habit.name"
        class="grid grid-cols-[180px_repeat(7,minmax(40px,1fr))] gap-2 items-center min-w-[520px]"
      >
        <div class="flex items-center gap-2 text-sm text-zinc-400">
          <span>{{ habit.emoji }}</span>
          <span>{{ habit.name }}</span>
        </div>
        <div
          v-for="i in 7"
          :key="`${habit.name}-${i}`"
          :class="[
            'h-10 rounded-xl border',
            i % (index + 2) === 0 ? 'bg-white border-white' : 'bg-zinc-950 border-zinc-800',
          ]"
        ></div>
      </div>
    </div>
  </div>
</template>

<script setup>
const { habits } = defineProps({
  habits: {
    type: Array,
    required: true,
  },
})
</script>
