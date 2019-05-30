<script>
    let title = 'Taggerati';
    let tagJSON = { 
            "apple": 2,  
            "accenture": 45,
            "ibm": 3
            };
</script>

<style>

    .tag-box {
		border: 1px solid #d3d3d3;
        display: inline-block;
        padding: .75em;
        cursor: pointer;
	}

    .tag { 
        border: .5px solid gray;
        color: white;
        display: inline-block;
        padding: .5em;
        cursor: pointer;
        font-size: .75em;
        border-radius: .25em;
        background-color: dodgerblue;

    }
</style>
<h1>{title}</h1>

<div class="tag-box">
    <div class="tag">Apple</div>
    <div class="tag">Microsoft</div>
    <div class="tag">IBM</div>
    <input class="tagsInput">
</div>
