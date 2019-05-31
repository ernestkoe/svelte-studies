<script>
	export let name;

	let rando;

	function setRando(){
		rando = Math.random()
	}

	import Surname from "./Surname.svelte";
	import UserInfo from "./UserInfo.svelte";
	import Noter from "./Noter.svelte";
	import Taggerati from "./Taggerati.svelte";
	import Msgbox from "./Msgbox.svelte";	
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
<h1>Svelte Demos</h1>
<p>hello {name}!</p>
<p><button on:click={setRando}>Click to generate a random number</button>
<p>The random number is {rando}</p>
<Taggerati/>
<UserInfo surname="Two" />
<Msgbox />

</div>

