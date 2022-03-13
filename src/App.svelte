<script>
	import Clicked from "./components/reactivity/Clicked.svelte";
	import Nested from "./components/props/Nested.svelte";
	import KidInfo from "./components/props/KidInfo.svelte";
	import CheckInStatus from "./components/logic/CheckInStatus.svelte";
	export let name;
	let message = "This is a new nested message";

	const kids = [
		{
			name: "Louis",
			age: "3.5",
			favColor: "pink",
			favThing: "trains",
			imgSrc: "./images/louis.jpg"
		},
		{
			name: "Viggo",
			age: "4.5",
			favColor: "yellow",
			favThing: "cars",
			imgSrc: "./images/viggo.jpg"
		},
		{
			name: "Solvej",
			age: "5.5",
			favColor: "blue",
			favThing: "Horses",
			imgSrc: "./images/solvej.jpg"
		},
			]


</script>

<main>
	<h1>Hello {name}!</h1>
	<!--<Nested message = {message}/>
	<Nested/> -->
	<Clicked/>

	<div class="row">
	{#each kids as kid, i}
		<div class="card">
			<h1>{kid.name}</h1>
		<CheckInStatus name = {kid.name} kidImg = {kid.imgSrc}/>
		<KidInfo name={kid.name} age = {kid.age} favColor = {kid.favColor} favThing = {kid.favThing}/>
		</div>
		<br><br>
	{/each}
	</div>
</main>



<style>
	.row {
		display: flex;
		flex-direction: row;
	}
	.card {
		background-color: lightblue;
		border-radius: 50px;
		padding: 20px 20px;
		max-height: fit-content;
		width: 400px;
		margin: 1em;
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

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>