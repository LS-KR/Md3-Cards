<script lang="ts">
import { marked } from 'marked'
import { Vue, Component, Prop } from 'vue-facing-decorator'

@Component({})
export default class MDCard extends Vue {
    @Prop({required: true}) title!: string;
    @Prop({required: true}) description!: string;
    @Prop({required: true}) image!: string;
    @Prop({required: false}) alt!: string;

    md = "";

    mounted() {
        this.md = marked(this.description).toString()
    }
}
</script>

<template>
    <div class="mdc-card">
        <div class="left">
            <img :src="image" :alt="alt" />
        </div>
        <div class="right">
            <h1 v-text="title" />
            <div v-html="md" class="markdown" />
        </div>
    </div>
</template>

<style lang="scss">
.mdc-card {
    margin: 1rem 2rem;
    display: flex;
    flex-direction: row;
    gap: 1rem;
    border-radius: 3rem;
    background: #f2cdcd;
    width: calc(100% - 4rem);
    min-height: 200px;
    padding: 1rem;

    .left {
        width: 250px;
        height: 100%;
        display: block;
        object-fit: cover;
        object-position: center;

        img {
            border-radius: 15%;
            object-fit: cover;
            object-position: center;
            max-width: 250px;
            max-height: 250px;
        }
    }

    .right {
        width: 100%;
        height: 100%;
        display: block;

        h1 {
            font-size: 2rem;
            margin-bottom: 0.2rem;
            border-bottom: #5c5f77 solid 1px;
            color: #5c5f77;
        }

        .markdown {
            width: 100%;
            height: 100%;
            display: block;
            color: #4c4f69;

            p {
                color: #4c4f69;
            }

            blockquote {
                color: #4c4f69;
                background-image: repeating-linear-gradient(45deg, #5bcefa3e, #5bcefa3e 10px, #faa0b93e 10px, #faa0b93e 20px, #ffffff3e 20px, #ffffff3e 30px, #faa0b93e 30px, #faa0b93e 40px);
                margin: 2em 0;
                padding-left: 20px;
                border-left: 3.5px solid #dc8a78;
                border-radius: 7.5px;
            }
        }
    }
}
</style>