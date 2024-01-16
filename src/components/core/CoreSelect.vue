<template>
  <div>
    <span>{{ label }}</span>
    <select v-model="selectValue" @change="seletItem">
      <option v-for="item in dataSource" :key="item.id" :value="item">
        {{ item.name }}
      </option>
    </select>
  </div>
</template>

<script setup>
import { ref, defineEmits, defineProps } from "vue";

const selectValue = ref("");

const props = defineProps({
  label: {
    type: String,
    default: "",
  },
  dataSource: {
    type: Array,
    default: [],
  },
});

const emit = defineEmits(["emitedSelectedValue"]);

const seletItem = () => {
  emit("emitedSelectedValue", selectValue.value);
};
</script>
