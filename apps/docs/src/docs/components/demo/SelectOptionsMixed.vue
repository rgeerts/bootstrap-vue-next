<template>
  <BFormSelect
    v-model="selected"
    :options="exFirstSlotOptions"
    class="mb-3"
  >
    <!-- This slot appears above the options from 'options' prop -->
    <template #first>
      <BFormSelectOption
        :value="null"
        disabled
        >-- Please select an option --</BFormSelectOption
      >
    </template>

    <!-- These options will appear after the ones from 'options' prop -->
    <BFormSelectOption value="C">Option C</BFormSelectOption>
    <BFormSelectOption value="D">Option D</BFormSelectOption>
  </BFormSelect>

  <div class="mt-3">
    Selected: <strong>{{ selected }}</strong>
  </div>
</template>

<script setup lang="ts">
import {ref} from 'vue'

const exFirstSlotOptions = [
  {value: 'A', text: 'Option A (from options prop)'},
  {value: 'B', text: 'Option B (from options prop)'},
]

const selected = ref(null)
</script>
