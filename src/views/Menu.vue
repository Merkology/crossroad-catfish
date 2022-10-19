<template>
  <!-- entire page -->
  <main class="flex min-h-screen w-full items-center justify-center">
    <!-- tabs -->
    <div
      class="grid w-1/6 grid-cols-2 space-x-2 rounded-xl bg-gray-200 p-0"
      x-data="app"
    >
      <div>
        <input
          type="radio"
          name="option"
          id="1"
          value="Inbound"
          v-model="selected"
          class="peer hidden"
          checked
        />
        <label
          for="1"
          class="block cursor-pointer select-none rounded-xl p-4 text-center peer-checked:bg-blue-500 peer-checked:font-bold peer-checked:text-white"
          >Inbound</label
        >
      </div>

      <div>
        <input
          type="radio"
          name="option"
          id="2"
          value="Outbound"
          v-model="selected"
          class="peer hidden"
        />
        <label
          for="2"
          class="block cursor-pointer select-none rounded-xl p-4 text-center peer-checked:bg-blue-500 peer-checked:font-bold peer-checked:text-white"
          >Outbound</label
        >
      </div>
    </div>
  </main>
  <div class="flex justify-center">
    <span class="text-lg strong">Value: {{ selected }}</span>
  </div>

  <ul>
    <li v-for="item in filteredList" :key="item.id">
      <span>{{ item.model }}</span>
    </li>
  </ul>
</template>

<script setup>
import { ref, watch, onMounted } from "vue";

// variables //
const selected = ref("Inbound");
const arr = ref([
  { model: "Yealink", type: "Inbound" },
  { model: "Polycom", type: "Outbound" },
  { model: "Cisco", type: "Inbound" },
  { model: "Grandstream", type: "Outbound" },
  { model: "Aastra", type: "Inbound" },
  { model: "Panasonic", type: "Outbound" },
]);
const filteredList = ref([]);

// watchers //
watch(selected, (val) => {
  filter(val);
});

const filter = (data) => {
  console.log(data);
  filteredList.value = arr.value.filter((item) => item.type === data);
  console.log("filtered list", filteredList.value);
};

onMounted(() => {
  filter("Inbound");
});
</script>
