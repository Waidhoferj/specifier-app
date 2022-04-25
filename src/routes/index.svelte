<script lang="ts">
    import Prompt from "$lib/Prompt.svelte"
	

</script>


<main>
    <div class="timeline"></div>
    <div class="content">
    <div class="spacer"></div>
    <Prompt/>
    </div>
    
</main>


<style global>


main {
    display: flex;
    justify-content: center;
}

.spacer {
    width: 100%;
    height: 100px;

}

html,
body {
	font-family: 'Inter', sans-serif;
	margin: 0;
    background-color: #E5EFF8;
}

.timeline {
    position: fixed;
    top:50px;
    left: 50%;
    height: 100vh;
    border: 1px solid rgb(152, 197, 248);
}

.content {
position: relative;
width: 90%;
max-width: 800px;
}


button,
input[type='submit'] {
	transform: scale(1);
	transition: transform 0.4s;
	border: none;
	border-radius: 11px;
	background-color: #529FF9;
	padding: 12px 30px;
	color: white;
	font-weight: 700;
	font-size: 17px;
	cursor: pointer;
	-webkit-appearance: none;
	-moz-appearance: none;
	appearance: none;

    margin: 20px auto;

	
}

button.wrapper {
    padding: 0;
    background-color: transparent;
}

button:active {
    transform: scale(0.95);
}

textarea {
    width: 100%;
    resize: vertical;
}

button.wrapper {
		margin: 0;
		padding: 0;
		border-radius: 0;
		background-color: transparent;
	}

	button:active {
		transform: scale(0.95);
	}
	button:active:disabled {
		transform: scale(1);
	}

	button:disabled {
		background-color: gray;
	}

input,
textarea {
	display: block;
	border-radius: 12px;
	background-color: #ededed;
	border: 1px solid #cdcdcd;
	padding: 10px;
	font-family: 'IBM Plex Sans', sans-serif;
	font-size: 15px;
}
</style>