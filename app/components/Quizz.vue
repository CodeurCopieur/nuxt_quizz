<script setup>
  const props = defineProps({
    quizz: {
      type: Object,
      required: true
    }
  })

  const step = ref(0)

  const { quizz } = toRefs(props)
</script>

<template>
    <h1>{{ quizz.title }}</h1>
    <Progress :value="step" :max="quizz.questions.length - 1" />
</template>

<style lang="scss" scoped>
  
</style>