<script>
	// @ts-nocheck

	export let addNewCar;
	export let image;
	export let brand;
	export let model;
	export let year;

	const onSubmit = () => {
		addNewCar(brand, model, year, image);
		resetForm();
	};

	const resetForm = () => {
		brand = '';
		model = '';
		year = '';
		image = '';
	};
</script>

<form on:submit|preventDefault={onSubmit}>
	<div class="input-container">
		Značka: <input type="text" bind:value={brand} />
		Model: <input type="text" bind:value={model} />
		Rok výroby: <input type="text" bind:value={year} />
		Obrázek:
		<input type="file" id="inputFile" />
	</div>
	<button disabled={!brand || !model || !year} type="submit" class="add-button"> Vložit </button>
</form>

<style>
	.input-container {
		display: inline-grid;
		margin: 2rem;
	}

	.add-button {
		float: right;
		margin-right: 2rem;
		margin-top: 9rem;
	}
</style>
