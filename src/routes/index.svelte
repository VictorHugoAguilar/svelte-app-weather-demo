<script>
	import { getWeatherFrom } from '../services/weather.js';
	import WeatherFooter from '../components/weather-footer.svelte';
	import WeatherIcon from '../components/weather-icon.svelte';

	let response = getWeatherFrom('Murcia');

	function handlerChangeInput(event) {
		const { value } = event.target;
		if (value.length > 0) {
			response = getWeatherFrom(value);
		}
	}
</script>

<div class="index">
	<div class="header">
		<h1>
			<slot name="title">
				<span>App Weather</span>
			</slot>
		</h1>
	</div>

	<div class="searchCity">
		<div class="form-group">
			<label for="city">Search City</label>
			<input
				on:change={handlerChangeInput}
				type="text"
				class="form-control"
				id="city"
				placeholder="Enter city"
			/>
		</div>
	</div>

	<div class="center">
		{#await response then weather}
			<section>
				<div class="nameCity">
					<h1>{weather.locationName}</h1>
				</div>
				<div class="temperatureCity"> 
					<h2>{weather.temperature}º</h2>
					<h3>{weather.conditionText}</h3>
				</div>					
				<WeatherIcon text={weather.conditionText} icon={weather.conditionIcon} />
			</section>
			<WeatherFooter humidity={weather.humidity} windSpeed={weather.windSpeed} feelLike={weather.feelsLike}/>
		{/await}
	</div>
</div>

<style>
	.index {
		margin: 0;
	}

	.header {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-bottom: 1rem;
	}

	.searchCity {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-bottom: 1rem;
	}

	.center{
		display: flex;
		margin-bottom: 1rem;
	}

	.nameCity{
		width: 100%;
		display: flex;
		justify-content: left;
		align-items: center;
		margin-bottom: 1rem;
	}

	.temperatureCity{
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 1rem;
	}

	section {
		padding: 16px;
		width: 100%;
	}

	h1 {
		font-weight: 300;
		color: #333;
		text-transform: uppercase;
		padding: 16px 0 0 0;
	}

	h2 {
		font-weight: 300;
		font-size: 120px;
		color: #333;
		text-transform: uppercase;
		padding: 0;
	}

	h3 {
		font-weight: 700;
		transform: rotate(-90deg);
	}
</style>
