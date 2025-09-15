<script setup>

const quizz = ref(null)
const state = ref('loading')
onMounted(() => {
    fetch('/quizz.json')
        .then(res => {
            if (!res.ok) {
                throw new Error('Impossible de charger le json')
            }
            return res.json()
        })
        .then(data => {
            quizz.value = data
            state.value = 'loaded'
        })
        .catch(err => {
            state.value = 'error'
        })
})

</script>
<template>
    <div class="container">
        <div v-if="state === 'error'">
            <p>Erreur lors du chargement du quizz</p>
        </div>
        
        <div :aria-busy="state === 'loading'">
            <Quizz :quizz="quizz" />
        </div>
    </div>
</template>

<style>
    .container {
        margin-top: 1rem;
    }
</style>