<script lang="ts">
    import "@picocss/pico"
    let {stringi=$bindable(), analyzeString} = $props()
</script>

<div>
    <input placeholder="Text you want to analyze" bind:value={stringi}/>
    <button onclick={analyzeString}>Analyze!</button>
</div>

<style>
    div {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    input {
        margin-top: 1rem;
        margin-right: 1rem;
        min-width: 25%; 
    }
</style>