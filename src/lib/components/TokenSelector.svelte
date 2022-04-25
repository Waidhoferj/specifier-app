<script lang="ts">
    import {createEventDispatcher} from "svelte"
    import {EditIcon} from "svelte-feather-icons"
    let dispatch = createEventDispatcher<{edit: true}>()
    export let tokens: Token[];
    
    function selectToken(token: Token) {
        if(!token.wordType) return
        let i = tokens.findIndex(t => t == token)
        let curIndex = tokens.findIndex(t => t.selected)
        if(curIndex >= 0) tokens[curIndex].selected = false
        tokens[i].selected = true
    }
</script>


<p>
    {#each tokens as token}
<span 
    class:noun="{token.wordType === 'NOUN'}"
    class:verb="{token.wordType === 'VERB'}"
    class:selected="{token.selected}"
    on:click="{() => selectToken(token)}"
>{token.word + " "}</span>
{/each}
</p>


<style>

    p {
        border-left: 2px solid blue;
        padding: 10px;
        background-color: #eef7ff;
        font-style: italic;
    }
.noun, .verb {
            cursor: pointer;
        }

        .noun {
            color: #2b7fdf;
        }

        .verb {
            color: #FE5723;
        }
</style>
