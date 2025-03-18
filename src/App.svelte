<script lang="ts">
  import "@picocss/pico"
  import SentimentAnalysis from "./lib/sentiment-analysis/sentiment-analysis.svelte"
</script>

<main>
  <h1 id="sentiment-analysis-h1">Sentiment Analysis Service</h1>
  <SentimentAnalysis/>
</main>

<style>
  #sentiment-analysis-h1 {
    margin-bottom: 3rem;
    text-shadow: 2px 2px 3px rgba(0,0,0,0.3);
  }
</style>
