<script lang="ts"> 
    import Card from "$lib/components/Card.svelte"
    import SubmissionField from "$lib/components/SubmissionField.svelte"
    import TokenSelector from "$lib/components/TokenSelector.svelte"

    export let word: Token;
    let selectedSpecifier: Token | null = null 
    
    $: selectedSpecifier = word?.specification.find((el) => el.selected)

</script>


    <Card>
        <h3 class="question">
            {#if word.wordType == "NOUN"}
                which <span class="key-word">{word.word}</span> specifically?
                {:else}
                <span class="key-word">{word.word}</span> how specifically?
            {/if}
        </h3>
        

       
    {#if word.specification.length}
        <TokenSelector bind:tokens={word.specification} on:edit={() => word.specification = []}/>
        {:else}
        <SubmissionField on:submit={event => word.specification = event.detail} />
        {/if}
    </Card>

    {#if selectedSpecifier}
    <svelte:self bind:word={selectedSpecifier}/>
    {/if}



<style>
    .question {
        font-size: 25px;
        font-weight: 500;
    }

    .key-word {
        font-weight: bold;
    }

</style>
