<script setup>
  const props = defineProps({
    answers: {
      type: Array,
      required: true
    }
  })

  const { answers } = toRefs(props)
</script>

<template>
    <div class="recap">
        <h2>Récapitulatif</h2>
        <ul>
            <li v-for="(answer, index) in answers" :key="index">{{ answer }}</li>
        </ul>
    </div>
</template>

<style>
  .recap {
    padding-top: 2rem;
  }

  .recap ul {
    list-style: none;
  }

  .recap ul li {
    margin-bottom: 1rem;
  }

  .recap ul li:last-child {
    margin-bottom: 0;
  }
</style>