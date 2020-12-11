<script>

	let interestRate = 3;
	let loanAmount = 200000;
	let years = 30;
	const MONTHS_PER_YEAR = 12;

	$: months = years * MONTHS_PER_YEAR;
	$: monthlyInterestRate = interestRate / 100 / MONTHS_PER_YEAR;
	$: numerator = loanAmount * monthlyInterestRate;
	$: denominator = 1 - (1 + monthlyInterestRate) ** -months;
	$: payment =  !loanAmount || !years ? 0 : interestRate ? numerator / denominator : loanAmount / months;
</script>

<div class="hero-image">
	<div class="hero-text">
		<h1>Loans Check</h1>
		<p>Check how much money you can get right now</p>
		<button>Loans Check</button>
	</div>
</div>
<div class=" text-center" style="padding-bottom: 50px">
	<div class="row">
		<h1>Loan Calculator</h1>
		<p>Use our calculator to calculate your wealth</p>
	</div>

</div>
<div class="container">
	<div class="row text-center">
			<h2>Enter configure your plan</h2>
			<p class="text-info">Given the status of your loan we can make things easier!</p>
	</div>
			<div class="card">
				<img height="100px" src="https://images.unsplash.com/photo-1462206092226-f46025ffe607?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1506&q=80" alt="loans">
				<div class="card-body">
					<label for="loan">LOANS</label>
					<input class="input-group" id="loan" type="number" bind:value={loanAmount}>

					<label for="interest">Interest</label>
					<input class="input-group" id="interest" type="number" bind:value={interestRate}>

					<label for="years">LOANS</label>
					<input class="input-group" id="years" type="number" bind:value={years}>
				</div>

				<div class="card-footer">
					Monthly Payment: ${payment.toFixed(2)}
				</div>
		</div>


</div>
<footer>
</footer>

<style>
	body, html {
		height: 100%;
	}
	.hero-image {
		background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('https://source.unsplash.com/random');
		height: 50%;

		background-position: center;
		background-repeat: no-repeat;
		background-size: cover;
		position: relative;
	}
	.hero-text {
		text-align: center;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		color: white;
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	footer {
		width: 100%;
		height: 300px;
		background-color: #02122b;
		color: #ffffff;

	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
