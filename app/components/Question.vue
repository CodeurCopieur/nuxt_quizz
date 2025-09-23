<script setup>
  const props = defineProps({
    question: {
      type: Object,
      required: true
    }
  })

  const { question } = toRefs(props)

  const emit = defineEmits(['answer'])

  const answer = ref(null)
</script>

<template>
    <div class="question">
        <h3>{{ question.question }}</h3>
        <ul>
            <li 
                v-for="(choice, i) in question.choices" 
                :key="choice">

                <label :for="`choice-${i}`">
                    <input type="radio" 
                        :id="`choice-${i}`" 
                        :name="question.question"
                        v-model="answer" 
                        :value="choice" />
                    {{ choice }}
                </label>

            </li>
        </ul>
        {{ answer }}
        <button class="btn btn-primary">Suivant</button>
    </div>
</template>

<style>
  .question {
    padding-top: 2rem;
  }

  .question button {
    margin-left: auto;
    display: block;
  }
</style>