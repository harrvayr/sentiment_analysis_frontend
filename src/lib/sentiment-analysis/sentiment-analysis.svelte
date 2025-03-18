<script lang="ts">
    import type { JsonResponse } from "../../types/sentiment-analysis";
    import AnalysisAnswer from "./analysis-answer.svelte";
    import TextInput from "./text-input.svelte";

    let userText: string = $state("")
    let analysisAnswer: string = $state("")
    let result: JsonResponse | undefined = $state()


    async function doPost () {
		const res = await fetch('https://httpbin.org/post', {
			method: 'POST',
			body: JSON.stringify({
				"sentiment": userText,
				"analysis": analys()
			})
		})
		
		const json = await res.json()
		result = {textToAnalyze: json.json.sentiment, analysis: json.json.analysis}
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
    <TextInput bind:stringi={userText} analyzeString={doPost}></TextInput>
    <AnalysisAnswer answer={result?.analysis}></AnalysisAnswer>
</div>

