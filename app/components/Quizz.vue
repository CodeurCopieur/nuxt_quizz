<script setup>
  const props = defineProps({
    quizz: {
      type: Object,
      required: true
    }
  })

  const step = ref(0)

  const { quizz } = toRefs(props)
  const currentQuestion = computed(() => quizz.value.questions[step.value])

  const arrayAnswers = ref(props.quizz.questions.map(() => null))

  const addAnswer = (answer, index) => {
    arrayAnswers.value[step.value] = answer
    if (step.value === quizz.value.questions.length - 1) {
      state.value = 'recap'
    } else {
      step.value++  
    }
  }

  const state = ref('question')
</script>

<template>
    <h1>{{ quizz.title }}</h1>
    <Progress :value="step" :max="quizz.questions.length - 1" />
    <Question :question="currentQuestion" v-if="state === 'question'" @answer="addAnswer" />
    <Recap :answers="arrayAnswers" v-if="state === 'recap'" />
</template>