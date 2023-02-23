<script>
	// @ts-nocheck
	export let selectedCar;
	export let arrayOfCars;
	export let selectCarDetail;
	export let deleteCar;
</script>

<div class="cars-list">
	<h3 class="cars-header">Seznam vozidel</h3>
	{#each arrayOfCars as car}
		<div>
			<!-- <a
                href={car.brand}
                on:click={selectDetailCar(car)}
                class={selectedCar === car ? 'selected' : 'select-button'}
            >
                {car.brand} {car.model} {car.year}</a
            > -->

			<button
				on:click={selectCarDetail(car)}
				class={JSON.stringify(selectedCar) === JSON.stringify(car) ? 'selected' : 'select-button'}
				>{car.brand} {car.model} {car.year}</button
			>
			<button on:click={deleteCar(car)} class="delete-button">X</button>
		</div>
	{/each}
</div>

<style>
	.delete-button {
		border: 0;
		background: transparent;
		width: 1rem;
		height: 1rem;
		margin-right: 2rem;
		border-radius: 50%;
		float: right;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.delete-button:hover {
		background: red;
		color: white;
		border-radius: 50%;
	}

	.select-button {
		margin-left: 2rem;
		border: 0px;
		background: transparent;
		color: black;
		text-decoration: none;
	}
	.select-button:hover {
		background: #e6e6e6;
	}

	.selected {
		margin-left: 2rem;
		border: 0px;
		background: transparent;
		background: #e6e6e6;
	}

	.cars-list {
		border-right: 1px solid black;
		width: 50%;
		padding-bottom: 1rem;
	}

	.cars-header {
		margin-left: 2rem;
	}
</style>
