<template>
  <h1 class="text-center">Expedición</h1>

  <v-sheet class="d-flex mx-auto mt-6" max-width="800">
    <v-sheet width="100%">
      <h5 class="text-center text-h5">States</h5>

      <v-sheet class="filters-container">
        <v-checkbox hide-details v-for="state in states" :key="state.id" v-model="state.selected"
          :label="state.name"></v-checkbox>
      </v-sheet>

      <button @click="submit">click me!</button>
    </v-sheet>

    <v-sheet width="100%">
      <h5 class="text-center text-h5">Filters</h5>

      <div>
        <v-select :items="filters" v-model="selected" density="compact" label="Compact"></v-select>
      </div>
    </v-sheet>

  </v-sheet>
</template>

<script setup>
import { ref } from 'vue';

const DEFAULT_STATES = [
  { id: 1, name: "First", selected: false },
  { id: 2, name: "Second", selected: false },
];
const DEFAULT_FILTERS = ["hardcoded-1", "hardcoded-2"];
const states = ref(DEFAULT_STATES);
const filters = ref(DEFAULT_FILTERS);
const selected = ref(filters.value[0]);
const submit = () => {
  console.log("states", states.value);
  console.log("selectedFilter", selected.value);
}

</script>

<style>
.filters-container .v-selection-control {
  min-height: auto;
}
</style>