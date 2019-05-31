<script>
  let title = "Taggerati";
  let mytags = {};
  let input = "";
  let selectedTag = "";
  let selectedDisplay = "selected-display-off";
  var dump = "";
  var tagRegex = /\s*[,;]+\s*|[,;]+|\s+/;
  const tagValidRegex = /^[^ ;,]+$/;
  const tagInputTrigger = "Enter";

  function handleInput() {
    let theKey = event.key;
    //let theKeyCode = event.keyCode;
    dump = input.split(tagRegex);

    // listen for the trigger key, if we find it, process all of input as tags
    if (theKey == tagInputTrigger) {
      input
        .split(tagRegex)
        .forEach(x => (tagValidRegex.test(x) ? (mytags[x] = true) : null));
      input = "";
    }
  }

  function deleteTag(tag) {
    delete mytags[tag];
    console.log(JSON.stringify(mytags));
    mytags = mytags;
    selectedDisplay = "selected-display-off";

  }

  function selectTag(tag) {
    //let theTagObject = mytags[tag];
    console.log(JSON.stringify(mytags[tag]));
    selectedDisplay = "selected-display-on";
    selectedTag = tag;
  }
</script>

<style>
  .dump {
    display: block;
    margin: 0.2em;
    padding: 0.5em;
    font-family: "Courier New", Courier, monospace;
    font-size: 75%;
  }

  .label {
    display: block;
    padding: 0.5em;
    font-size: 0.75em;
  }

  .tag-box {
    width: 320px;
    min-height: 3em;
    border: 1px solid #d3d3d3;
    display: inline-block;
    padding: 0.5em;
    cursor: pointer;
  }

  .tag-box .tag {
    display: inline-block;
    padding: 0.75em;
    padding-right: 1em;
    padding-left: 1em;
    margin-inline-end: 0.2em;
    margin: 0.2em;
    border: 0.5px none;
    color: darkslategray;
    cursor: pointer;
    font-size: 0.75em;
    border-radius: 0.4em;
    background-color: #eeeeee;
  }

  .tag-box .tag:hover {
    background-color: #3af;
    color: whitesmoke;
  }

  .tag-box .tag .close::after {
    content: "×";
    font-weight: bold;
    display: inline-block;
    transform: scale(1.4);
    margin-left: 0.75em;
  }

  .tag-box .tag-input {
    margin-left: 0.2em;
    margin-right: 0.2em;
    margin-bottom: 0.8em;
    border: 0.5px solid #d3d3d3;
    border-radius: 0.25em;
    display: block;
  }

 .tag-box .selected-display-off {
    display: none;
  }

 .tag-box .selected-display-on {
    display: inline-block;
    padding: 0.75em;
    padding-right: 1em;
    padding-left: 1em;
    margin-inline-end: 0.2em;
    margin: 0.2em;
    border: 0.5px none;
    border-color: darkslategray;
    background-color: lightslategray;
    color: white;
    border-radius: 0.1em;
    font-size: 0.75em;
  }

</style>

<h1>{title}</h1>
<div class="tag-box">
  <div class="label">Add tags, hit enter:</div>
  <input class="tag-input" bind:value={input} on:keyup={handleInput} />
  <!--
    <div class="tag">Apple</div>
    <div class="tag">Microsoft</div>
    <div class="tag">IBM</div>
   -->
  {#each Object.keys(mytags) as tag}
    <div id={tag} class="tag" on:click={() => selectTag(tag)}>
       {tag}
      <span class="close" on:click={() => deleteTag(tag)} />
    </div>
  {/each}
  <div class="dump">input split: {dump}</div>
  <div id="selectedTag" class={selectedDisplay}>
    selected Tag: {selectedTag}
  </div>

</div>
