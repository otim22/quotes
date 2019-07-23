<template>
  <div id="container">
    <div class="row">
      <app-header :quoteCount="quotes.length" :maxQuote="maxQuote"></app-header>
      <app-new-quote @quoteAdded="newQuote($event)"></app-new-quote>
      <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote($event)"></app-quote-grid>
    </div>
    
    <div class="row">
      <div class="col sm-12 textcenter">
        <div class="alert alert-info">
          Info Click on a quote to delete it!
        </div>
      </div>
    </div>
  </div>
</template>

<script>

  import QuoteGrid from './components/QuoteGrid.vue';
  import NewQuote from './components/NewQuote.vue';
  import Header from './components/Header.vue';

  export default {
    data: function() {
      return {
        quotes: [
          'First quote to display'
        ],
        maxQuote: 10
      }
    },
    methods: {
      newQuote(quote) {
        if(this.quotes.length >= this.maxQuote) {
          return alert('Please delete Quotes first');
        }
        this.quotes.push(quote);
      },
      deleteQuote(index) {
        this.quotes.splice(index, 1)
      }
    },
    components: {
      appQuoteGrid: QuoteGrid,
      appNewQuote: NewQuote,
      appHeader: Header
    }
  }
</script>

<style>

</style>
