<script lang="ts">
import MDCard from '@/components/MDCard.vue'
import { CardData } from '@/logic/data'
import { Vue, Component } from 'vue-facing-decorator'
import cards from '@/data/cards.json'

@Component({components: {MDCard}})
export default class App extends Vue {
    cards = cards as CardData[]
}
</script>

<template>
    <div class="container">
        <MDCard v-for="card of cards" :key="card.title" :title="card.title" :description="card.description" :image="card.image" :alt="card.alt" />
    </div>
</template>

<style lang="scss">
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    margin: auto;
    min-height: 100vh;
    max-width: 900px;
}

body {
    background: #efebe9;
}

.container {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: start;
    justify-items: start;
}
</style>
