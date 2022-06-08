<script setup lang="ts">
import { ref } from "vue";
import Table from "./Table.vue";

defineProps<{ msg: string }>();

const count = ref(0);
</script>

<template>
  <Table>
    <template
      v-for="(_, name) in ($slots as Pick<typeof $slots, 'default'| 'actions'| 'expanded'>)"
      v-slot:[name]="slotData"
    >
      <slot :name="name" v-bind="slotData" />
    </template>
  </Table>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
