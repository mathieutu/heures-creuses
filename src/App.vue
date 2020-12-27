<template>
  <div
    class="flex flex-col justify-center min-h-screen py-12 bg-gray-50 sm:px-6 lg:px-8"
  >
    <div class="text-center sm:mx-auto sm:w-full sm:max-w-md">
      <span class="text-7xl">⚡️</span>
      <h1 class="mt-6 text-3xl font-extrabold text-gray-900">
        Calculateur <br />
        Heures Creuses / Pleines
      </h1>
    </div>

    <div class="mt-8 sm:mx-auto sm:w-full sm:max-w-md">
      <div class="flex flex-col gap-4 px-4 py-8 bg-white shadow sm:rounded-lg sm:px-10">
        <div>
          <label for="abo" class="block text-sm font-medium text-gray-700">
            Prix abonnement
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              v-model="input.abo"
              type="number"
              id="abo"
              step="0.01"
              class="block w-full border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="0.00"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-8 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> €/mois </span>
            </div>
          </div>
        </div>
        <div>
          <label for="hp" class="block text-sm font-medium text-gray-700">
            Prix HP
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              v-model="input.hp"
              type="number"
              id="hp"
              step="0.01"
              class="block w-full border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="0.00"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-8 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> cts/kWh </span>
            </div>
          </div>
        </div>
        <div>
          <label for="hc" class="block text-sm font-medium text-gray-700">
            Prix HC
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              v-model="input.hc"
              type="number"
              id="hc"
              step="0.01"
              class="block w-full border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="0.00"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-8 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> cts/kWh </span>
            </div>
          </div>
        </div>
        <div>
          <label for="chp" class="block text-sm font-medium text-gray-700">
            Conso HP
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              v-model="input.chp"
              type="number"
              id="chp"
              step="1"
              class="block w-full border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="1000"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-8 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> kWh </span>
            </div>
          </div>
        </div>
        <div>
          <label for="chc" class="block text-sm font-medium text-gray-700">
            Conso HC
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              v-model="input.chc"
              type="number"
              id="chc"
              step="1"
              class="block w-full border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="1000"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-8 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> kWh </span>
            </div>
          </div>
        </div>
        <hr class="mx-10 my-6">
        <div>
          <label class="block text-sm font-medium text-gray-700">
            Total abonnement
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              :value="output.abo"
              type="text"
              disabled
              class="block w-full text-gray-500 bg-gray-100 border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> € </span>
            </div>
          </div>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700">
            Total HP
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              :value="output.hp"
              type="text"
              class="block w-full text-gray-500 bg-gray-100 border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> € </span>
            </div>
          </div>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700">
            Total HC
          </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              :value="output.hc"
              type="text"
              class="block w-full text-gray-500 bg-gray-100 border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> € </span>
            </div>
          </div>
        </div>
        <div>
          <label class="block text-sm font-medium text-gray-700"> Total </label>
          <div class="relative mt-1 rounded-md shadow-sm">
            <input
              :value="output.total"
              type="text"
              class="block w-full text-gray-500 bg-gray-100 border-gray-300 rounded-md focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            />
            <div
              class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none"
            >
              <span class="text-gray-500 sm:text-sm"> € </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent, reactive, computed } from "vue";

export default defineComponent({
  setup: () => {
    const format = nb => new Intl.NumberFormat('fr-FR', { style: 'currency', currency: 'EUR' }).format(nb)

    const input = reactive({});
    const output = computed(() => {
      const abo = input.abo * 12  || 0;
      const hc = (input.hc / 100) * input.chc || 0;
      const hp = (input.hp / 100) * input.chp || 0;

      return {
        abo: format(abo),
        hc: format(hc),
        hp: format(hp),
        total: format(abo + hc + hp),
      };
    });

    return {
      input,
      output,
    };
  },
});
</script>
