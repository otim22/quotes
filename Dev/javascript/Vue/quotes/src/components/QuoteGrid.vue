<template>
    <div class="row">
        <app-quote v-for="quote in quotes" :key="quote" @click.native="deleteQuote($event)">{{ quote }}</app-quote>
    </div>
</template>

<script>
    import Quote from './Quote.vue';

    export default {
        props: ['quotes'],
        components: {
            appQuote: Quote
        },
        methods: {
            deleteQuote(index) {
                this.$emit('quoteDeleted', index);
            }
        }
    }
</script>

<style>
    
</style>    