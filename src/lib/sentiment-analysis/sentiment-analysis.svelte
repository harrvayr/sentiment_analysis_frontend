<script lang="ts">
    import type { JsonResponse } from "../../types/sentiment-analysis";
    import AnalysisAnswer from "./analysis-answer.svelte";
    import SentimentInput from "./sentiment-input.svelte";

    let userSentiment: string = $state("s")
    let analysisAnswer: string = $state("")
    let result: JsonResponse | undefined = $state() 
	
    async function doPost () {
		const res = await fetch('https://httpbin.org/post', {
			method: 'POST',
			body: JSON.stringify({
				"sentiment": userSentiment,
				"analysis": analys()
			})
		})
		
		const json = await res.json()
		result = {sentiment: json.json.sentiment, analysis: json.json.analysis}
	}

    function analyzeS() {
        const n = Math.random()
        if(n<0.5){
            return "NEGATIVE"
        } else {
            return "POSITIVE"
        }
    }

    function analys(){
        analysisAnswer = analyzeS()
        return analysisAnswer
    }
     
</script>

<div>
    <SentimentInput bind:stringi={userSentiment} analyzeString={doPost}></SentimentInput>
    <AnalysisAnswer answer={result?.analysis}></AnalysisAnswer>
</div>

<style>
    div {
        border: 2px dotted red;
    } 
</style>