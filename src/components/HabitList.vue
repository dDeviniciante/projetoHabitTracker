<template>
  <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-6">
    <div class="flex flex-col gap-4 sm:flex-row sm:items-center sm:justify-between mb-6">
      <div>
        <p class="text-zinc-500 text-sm">Hoje</p>
        <h2 class="text-3xl font-bold mt-1">Seus hábitos diários</h2>
      </div>
      <div class="bg-zinc-950 border border-zinc-800 px-4 py-2 rounded-2xl text-sm text-zinc-400 w-fit">
        Quinta-feira
      </div>
    </div>

    <div class="space-y-3">
      <div
        v-for="habit in habits"
        :key="habit.name"
        class="bg-zinc-950 border border-zinc-800 rounded-2xl p-5 flex items-center justify-between gap-4 hover:bg-zinc-900 transition"
      >
        <div class="flex items-center gap-4 min-w-0">
          <div class="w-14 h-14 rounded-2xl bg-zinc-900 border border-zinc-800 flex items-center justify-center text-2xl shrink-0">
            {{ habit.emoji }}
          </div>
          <div class="min-w-0">
            <h3 class="font-semibold text-lg truncate">{{ habit.name }}</h3>
            <p class="text-zinc-500 text-sm mt-1">Sequência atual: {{ habit.streak }} dias</p>
          </div>
        </div>
        <button
          :aria-label="`Concluir hábito ${habit.name}`"
          class="w-8 h-8 rounded-xl border border-zinc-700 bg-zinc-900 hover:bg-white hover:border-white transition shrink-0"
        ></button>
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
