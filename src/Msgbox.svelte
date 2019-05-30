<script>
	const title = "Simple Chat Component";
	const author = "ernest.koe@proofgroup.com";
	let fdtx = "";
	let console = [];
	let input = "";
	
	function fdt(d1) {
		let fdtxHrs = ("0"+d1.getHours()).slice(-2);
		let fdtxMin = ("0"+d1.getMinutes()).slice(-2);
		let fdtxSec = ("0"+d1.getSeconds()).slice(-2);
		return fdtxHrs+":"+fdtxMin+":"+fdtxSec;
	}
	
	
	function setTextData() {
		// input = input.toUpperCase();
		if (event.key === 'Enter')
		{ 
			//let lastLine = input.substring(input.lastIndexOf("\n"),0);
			let lastLine = input.substring(input.lastIndexOf("\n", input.lastIndexOf("\n")-1));
			let theTS = fdt(new Date());
			console = [...console, {text: lastLine, ts: theTS }];
			input = "";
		}	
	}
</script>

<style>
	.block { 
		display: "inline-block" ;
	}
	
	.ts {
		display: "inline-block";
		padding-bottom: 0;
		font-size: .75em;
	}

	.item { 
	  display: "inline-block";
	  padding-bottom: 1em; 
	}
</style>

<div class="block">
<h1>{title}</h1>
	<p>
		This is a simple chat component demo of Sveltejs
	</p>
	<p>
		by: {author}
	</p>
		
	
</div>

<div class="block">
<label>Console</label>
{#each console as item}
<div class="ts">
	<p id="console"></p>
		{item.ts}
	</div>
	<div class="item">
		{item.text}
	</div>
{/each}
<textarea rows="4" cols="64" bind:value={input} on:keyup={setTextData}></textarea>
</div>

