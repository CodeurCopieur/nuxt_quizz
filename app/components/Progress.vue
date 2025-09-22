<script setup>
  defineProps({
    value: Number,
    max: Number
  })
</script>

<template>
    Etape {{ value + 1 }} / {{ max + 1 }}

    <div class="progress">
        <progress :value="value" :max="max"></progress>
    </div>
</template>

<style lang="scss" scoped>
  
</style>