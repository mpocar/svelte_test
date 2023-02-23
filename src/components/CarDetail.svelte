<script>
	// @ts-nocheck
	export let selectedCar;
	export let deleteCar;
</script>

<div class="car-detail">
	<h3 class="cars-header">Detail vozidla</h3>
	<div>
		{#if selectedCar}
			<div class="image-container">
				<img src={selectedCar.image} alt={selectedCar.brand} />
			</div>
			<h3 style="margin-left: 1rem">
				{selectedCar.brand}
				{selectedCar.model}
				{selectedCar.year}
			</h3>
			<button on:click={deleteCar(selectedCar)} class="delete-detail-button">Smazat</button>
		{/if}
	</div>
</div>

<style>
	.car-detail {
		width: 50%;
	}
	.cars-header {
		margin-left: 2rem;
	}
	.image-container {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 300px;
		width: 300px;
	}
	.delete-detail-button {
		float: right;
		margin-right: 2rem;
		margin-bottom: 1rem;
	}

	.delete-detail-button:hover {
		background: #e6e6e6;
	}
</style>
