<template>
  <SectionCard>
    <div class="space-y-4 items-center flex flex-col">
      <div class="text-red-500"><slot/></div>    
        <RoundButton @click="retry" v-if="retry">Retry Now</RoundButton>
    </div>
  </SectionCard>
</template>

<script setup>
import SectionCard from "./SectionCard.vue";
import RoundButton from "./RoundButton.vue";

defineProps({
retry: {
    type: Function,
    required: false   
}
})
</script>

<style lang="scss" scoped>

</style>