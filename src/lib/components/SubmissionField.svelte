<script lang="ts">
    import {createEventDispatcher, onMount} from "svelte"
    import axios from "axios"

    const dispatch = createEventDispatcher<{submit: Token[]}>()
    let submission: string = ""

    function onSubmit(e: Event) {
        let words = submission.split(" ")
        axios.post("https://specifier-4q2ga525ra-wl.a.run.app/parts-of-speech", {text: submission})
        .then(res => {
            let tokens: Token[] = res.data.tokens.map(({token, pos}) => ({
            word: token,
            wordType: pos,
            specification: [],
            selected: false
        }))
        dispatch("submit", tokens)
        }).catch(err => console.error(err))

        
    }

    function onKeypress(e: KeyboardEvent) {

        if(e.key == "Enter") {
            e.preventDefault()
            onSubmit(e)
        }
    }
</script>


<form on:submit|preventDefault={onSubmit}>
    <textarea name="specification" on:keypress={onKeypress} bind:value="{submission}"/>
    <input type="submit" value="Submit">
</form>


<style>
    textarea {
			resize: vertical;
			display: block;
			width: 100%;
			height: 100%;
            background-color: white;
            border-color: #C9C9C9;
            border-radius: 5px;
		}
</style>