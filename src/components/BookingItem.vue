<template>
  <SectionCard>
    <div class="flex justify-between">
      <div class="flex space-x-2">
        <div>{{ title }}</div>
        <div><component :is="icon" :class="{'animate-spin': pending}" /></div>
      </div>
      <RoundButton variant="danger" @click="$emit('cancelled')">Cancel</RoundButton>
    </div>
  </SectionCard>
</template>

<script setup>
import SectionCard from "./SectionCard.vue";
import RoundButton from "./RoundButton.vue";
import { LoaderCircle, Check } from "lucide-vue-next";
import { computed } from "vue";

const props = defineProps({
 title: String,
 status: String,
});

const pending = computed(() => props.status === "pending");
const icon = computed(() => (pending.value ? LoaderCircle : Check));

defineEmits(['cancelled'])

</script>

<style lang="scss" scoped>
</style>