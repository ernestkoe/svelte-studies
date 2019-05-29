<script>
	export let name;

	let rando;

	function setRando(){
		rando = Math.random()
	}

	import Surname from "./Surname.svelte";
	import UserInfo from "./UserInfo.svelte";
	import Noter from "./Noter.svelte";

	let input = "this is like magic";
	function setTextData() {
		input = input.toUpperCase();
		
	}
	
</script>

<style>


	h1 {
		color: purple;
	}

	.block { 
		display: "inline-block" ;
		padding: 2rem;
	}

</style>


<div class="block">
<h1>Hello {name}!</h1>
<button on:click={setRando}>Click to generate a random number</button>
<p>The random number is {rando}</p>
</div>


<div class="block">
<Surname />
<UserInfo name="something" surname={"foo"} />
<Noter />
</div>

