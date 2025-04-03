<script lang="ts">
    import type { JsonResponse } from "../../types/sentiment-analysis";
    import AnalysisAnswer from "./analysis-answer.svelte";
    import TextInput from "./text-input.svelte";

    let userText: string = $state("")
    let analysisAnswer: string = $state("")
    let result: JsonResponse | undefined = $state()

//"http://localhost:8100/analyze"
    async function doPost () {
		const res = await fetch('https://cc-assignment4-cc-sentiment-analysis-backend.2.rahtiapp.fi/analyze', {
			method: 'POST',
            headers: {
                "Content-Type": "application/json",
                "Authorization": "Bearer eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJhdXRob3JpemVkIjoieWVzIn0.0xCgQyHl9bAtlZLKAkrI_ZIb3julu8p3kLq7E_Ytc9slytJOnzYPTdFze9CvgvvaiuvkFjEGiWHWbZFtlYLWXg"
            },
			body: JSON.stringify({
				"text": userText,
			})
		})
		
		const json = await res.json()
        console.log(json)
		result = {textToAnalyze: json["text"], analysis: json["sentiment"]}
	}

     
</script>

<div>
    <TextInput bind:stringi={userText} analyzeString={doPost}></TextInput>
    <AnalysisAnswer answer={result?.analysis}></AnalysisAnswer>
</div>

