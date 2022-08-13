<script>
	export let humidity = 0;
	export let windSpeed = 0;
	export let feelLike = 0;
</script>

<footer>
	<div>
		<span> {humidity} </span>
		<strong> Humidity </strong>
	</div>

	<div>
		<span> {windSpeed} </span>
		<strong> Windspeed </strong>
	</div>

	<div>
		<span> {feelLike}° </span>
		<strong> Feels like </strong>
	</div>
</footer>

<style>
	footer {
		border: 2px solid #000;
		padding: 12px 32px;
		width: 80%;
		margin: 0 auto;
		border-radius: 10px;
		display: flex;
		text-align: center;
		justify-content: space-evenly;
		position: absolute;
		left: 0;
		right: 0;
		bottom: 32px;
	}

	span {
		display: block;
		font-weight: 600;
		font-size: 14px;
	}

	strong {
		color: #444;
		font-size: 14px;
		font-weight: 500;
	}
</style>
