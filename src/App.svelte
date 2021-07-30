<script>
	import ListInput from "./components/ListInput.svelte";
	import SingleWord from "./components/SingleWord.svelte";
	import { jsPDF } from "jspdf";
	import "../public/fonts/GowunBatang-Bold-normal"
	import "../public/fonts/Inter-Bold-normal"

	let text;
	let list = [];
	let font = 'Inter';
	let showForm = true;

	var pdf = new jsPDF({
		orientation: 'p',
		unit: 'in',
		format: 'letter'
	});
	pdf.setFontSize(48);

			


	function handleList(){
        list = text.split("\n");
    }

	function savePDF(){
		console.log(list);
		pdf.setFont('Inter-Bold', 'normal');
		pdf.text(list,4,1, 'center');
		pdf.save("test.pdf");
	}
</script>

<main>
		{#if showForm}
			<div class="input">
				<p>A dead simple way to inputting a simple list of vocab words, and getting a quick and easy to print sheet. Simple select your font, type in your words once per line. PDF output coming soon, but in the mean time, simply click 'toggle form' to see your words in full screen and print directly.</p>
				<form class="inputForm">
					<label for="font">Pick a Font</label>
					<select bind:value={font} name="font">
						<option value="Inter">Inter</option>
						<option value="Style Script">Style Script</option>
						<option value="Gowun Batang">Gowun Batang</option>
					</select>

					<br />

					<textarea rows="25" cols="25" on:change={handleList} bind:value={text}></textarea>

					<br />

					<button on:click={savePDF}>Save PDF</button>
					<br />
					<button on:click={hideForm => showForm = !showForm}>Hide Form</button>
				</form>
			</div>
		{/if}
			
		<div class="output" id="output">
			<button on:click={hideForm => showForm = !showForm}> Toggle Form </button>
			{#each list as word}
				<SingleWord word={word} font={font}/>
				<hr />
			{/each}
		</div>

</main>

<style>
	main {
		display:grid;
		grid-template-columns: 30% 70%;
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
		padding-right: 5px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>