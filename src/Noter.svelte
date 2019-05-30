<script>
	let name = "Jim Bob";
	export let input = "this is like magic";
	function setTextData() {
		var dt = new Date().getTime()+": ";
		// input = input.toUpperCase();
		if (event.key === 'Enter') { 
			input += dt;
		}
	}
	
</script>

<style>
</style>

<h3>{name},</h3>
	<p>Enter some notes here, we'll make everything upper case as you type:</p>
<label>Notes</label>
<textarea rows="20" cols="100" bind:value={input} on:keyup={setTextData}></textarea>
<p id="log"></p>
