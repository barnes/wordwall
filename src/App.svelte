<script>
	import ListInput from "./components/ListInput.svelte";
	import SingleWord from "./components/SingleWord.svelte";
	import html2pdf from 'svelte-html2pdf';

	let text;
	let list = [];
	let size;
	let font = 'Inter';

	function handleList(){
        list = text.split("\n");
    }

	function savePDF(){
		let element = document.getElementById('output');
		html2pdf(element);
	}
</script>

<main>
		<div class="input">
			<select bind:value={font} name="font">
				<option value="Inter">Inter</option>
				<option value="Style Script">Style Script</option>
				<option value="Gowun Batang">Gowun Batang</option>
			</select>


			<textarea rows="25" cols="25" on:change={handleList} bind:value={text}></textarea>

			<button on:click={savePDF}>Save PDF</button>
		</div>
			
		<div class="output" id="output">
			{#each list as word}
				<SingleWord word={word} font={font}/>
			{/each}
		</div>

</main>

<style>
	main {
		display:grid;
		grid-template-columns: 30% 70%;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4in;
		font-weight: 100;
	}

	.input {
		border-right: 5px solid black;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>