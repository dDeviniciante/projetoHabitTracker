<template>
  <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-6 space-y-6">
    <div>
      <p class="text-zinc-500 text-sm">Criar hábito</p>
      <h2 class="text-2xl font-semibold mt-1">Adicionar novo hábito</h2>
    </div>

    <div class="space-y-3">
      <label class="text-sm text-zinc-400">Qual hábito?</label>
      <div class="flex gap-3">
        <button class="w-14 h-14 rounded-2xl bg-zinc-950 border border-zinc-800 text-2xl hover:bg-zinc-800 transition shrink-0">📘</button>
        <input placeholder="Ex: Ler" class="flex-1 bg-zinc-950 border border-zinc-800 rounded-2xl px-4 outline-none min-h-[56px]" />
      </div>
    </div>

    <div class="space-y-3">
      <label class="text-sm text-zinc-400">Quantos dias na semana?</label>
      <div class="grid grid-cols-2 sm:grid-cols-4 lg:grid-cols-7 gap-2">
        <button
          v-for="(day, index) in weekdays"
          :key="day"
          :class="[
            'py-3 rounded-2xl text-sm font-medium transition',
            index <= 4 ? 'bg-white text-black' : 'bg-zinc-950 border border-zinc-800 text-zinc-500',
          ]"
        >
          {{ day }}
        </button>
      </div>
    </div>

    <div class="space-y-3">
      <label class="text-sm text-zinc-400">Como esse hábito será medido?</label>
      <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
        <button
          v-for="(metric, index) in metricTypes"
          :key="metric"
          :class="[
            'p-4 rounded-2xl text-left border transition',
            index === 2 ? 'bg-white text-black border-white' : 'bg-zinc-950 border border-zinc-800 hover:bg-zinc-800',
          ]"
        >
          {{ metric }}
        </button>
      </div>
    </div>

    <div class="space-y-3">
      <label class="text-sm text-zinc-400">Meta diária</label>
      <div class="flex gap-3">
        <input placeholder="20" class="flex-1 bg-zinc-950 border border-zinc-800 rounded-2xl px-4 py-4 outline-none" />
        <button class="bg-zinc-950 border border-zinc-800 rounded-2xl px-5 text-zinc-400 whitespace-nowrap">páginas</button>
      </div>
    </div>

    <div class="bg-zinc-950 border border-zinc-800 rounded-2xl p-4 space-y-2">
      <p class="text-sm text-zinc-400">Como o desempenho será calculado</p>
      <p class="text-sm text-zinc-500 leading-relaxed">
        Este hábito acontecerá apenas de segunda a sexta. O sistema calculará sua consistência apenas nesses dias.
      </p>
      <div class="flex items-center justify-between pt-2 text-sm gap-4">
        <span class="text-zinc-400">Dias esperados no mês</span>
        <span class="font-semibold text-white whitespace-nowrap">20 dias</span>
      </div>
    </div>

    <button class="w-full bg-white text-black py-4 rounded-2xl font-semibold hover:scale-[1.01] transition">Criar hábito</button>
  </div>
</template>

<script setup>
const { weekdays, metricTypes } = defineProps({
  weekdays: {
    type: Array,
    required: true,
  },
  metricTypes: {
    type: Array,
    required: true,
  },
})
</script>
