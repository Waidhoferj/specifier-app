<script lang="ts">
    import Card from "$lib/components/Card.svelte"
    import Specification from "$lib/Specification.svelte"
    import SubmissionField from "$lib/components/SubmissionField.svelte"
import TokenSelector from "./components/TokenSelector.svelte"
    let question: Token[] = []
    let selectedSpecifier: Token | null = null 
    
    $: selectedSpecifier = question.find((el) => el.selected)

</script>

<Card>
    <h1>Specifier</h1>
    <p>Look deeper into questions to achieve grounded answers. The specifier will prompt you to clarify any ambiguous terms in your statements. Start with a question or a goal and break it down into specific terms.</p>
    {#if question.length}
    <TokenSelector bind:tokens={question} on:edit={() => question = []}/>
        {:else}
        <SubmissionField on:submit={event => question = event.detail} />
    {/if}
    
</Card>

{#if selectedSpecifier}
    <Specification bind:word={selectedSpecifier}/>
{/if}

<style>
    h1 {
        font-size: 40px;
        margin-top: 0;
    }
</style>