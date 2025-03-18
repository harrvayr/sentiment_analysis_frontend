<script lang="ts">
    let {answer} = $props();
    let analyzed: boolean = $state(false);

    $effect(()=> {
        if(answer != undefined) {
            analyzed = true;
        }
    })
</script>

<div>
    {#if analyzed == true}
        <p>Sentiment is {answer}</p>
    {/if}
</div>