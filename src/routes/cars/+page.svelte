<script lang="js">
	// @ts-nocheck
	import CarsForm from '../../components/CarsForm.svelte';
	import CarDetail from '../../components/CarDetail.svelte';
	import CarList from '../../components/CarList.svelte';
	import { onMount } from 'svelte';

	let selectedCar;
	let arrayOfCars = [];
	let image;
	let brand = '';
	let model = '';
	let year = '';

	onMount(() => {
		if (localStorage.getItem('cars')) {
			arrayOfCars = JSON.parse(localStorage.getItem('cars'));
		}
		if (localStorage.getItem('selectedCar')) {
			selectCarDetail(JSON.parse(localStorage.getItem('selectedCar')));
		}
		const inputFile = document.querySelector('#inputFile');
		inputFile.addEventListener('change', (e) => {
			const file = e.target.files[0];
			const reader = new FileReader();
			reader.readAsDataURL(file);
			reader.onload = () => {
				image = reader.result;
			};
		});
	});

	const addNewCar = (brand, model, year, image) => {
		arrayOfCars = [...arrayOfCars, { brand, model, year, image }];
		selectCarDetail(arrayOfCars[arrayOfCars.length - 1]);
		document.getElementById('inputFile').value = '';
		setLocalSotrage();
	};

	const deleteCar = (car) => {
		arrayOfCars = arrayOfCars.filter((item) => item !== car);
		if (selectedCar === car) {
			selectedCar = null;
		}
		setLocalSotrage();
		localStorage.removeItem('selectedCar', JSON.stringify(selectedCar));
	};

	const selectCarDetail = (car) => {
		selectedCar = car;
		localStorage.setItem('selectedCar', JSON.stringify(selectedCar));
	};

	const setLocalSotrage = () => {
		localStorage.setItem('cars', JSON.stringify(arrayOfCars));
	};
</script>

<div class="index">
	<div class="main-container">
		<CarsForm {addNewCar} {image} {brand} {model} {year} />
		<div class="cars-container">
			<CarList {selectedCar} {arrayOfCars} {deleteCar} {selectCarDetail} />
			<CarDetail {selectedCar} {deleteCar} />
		</div>
	</div>
</div>

<style>
	.index {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.main-container {
		display: inline-table;
		border: 1px solid black;
		width: 60rem;
		height: 9rem;
	}

	.cars-container {
		border-top: 1px solid black;
		display: flex;
	}
</style>
