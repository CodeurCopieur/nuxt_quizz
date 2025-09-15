<script setup>
  const props = defineProps({
    quizz: {
      type: Object,
      required: true
    }
  })
</script>

<template>
    {{ quizz.title   }}
</template>

<style lang="scss" scoped>
  
</style>