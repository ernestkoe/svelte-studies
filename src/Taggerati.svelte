<script>
  let title = "Taggerati";
  let mytags = {};
  let input = "";
  let dump = "";
  const tagItKeys = [",", ";"];

  function handleinput() {
    let theKey = event.key;
    let theKeyCode = event.keyCode;
    if (tagItKeys.includes(theKey) || theKeyCode == 13) {
      input
        .split(theKey)
        .slice(0, -1)
        .forEach(x => (mytags[x] = true));
      input = "";
    }
    dump = theKeyCode;
  }
</script>

<style>
  .dump {
    display: block;
    margin: 0.2em;
    padding: .5em;
    font-family: 'Courier New', Courier, monospace;
    font-size: 75%;
  }

  .tag-box {
    width: 320px;
    min-height: 3em;
    border: 1px solid #d3d3d3;
    display: inline-block;
    padding: 0.5em;
    cursor: pointer;
  }

  .label {
    display: block;
    padding: 0.5em;
    font-size: 0.75em;
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
</style>

<h1>{title}</h1>
<div class="tag-box">
  <div class="label">Add tags (commas are separators):</div>
  <input class="tag-input" bind:value={input} on:keyup={handleinput} />
  <!--
    <div class="tag">Apple</div>
    <div class="tag">Microsoft</div>
    <div class="tag">IBM</div>
   -->
  {#each Object.keys(mytags) as tag}
    <div class="tag">
      {tag}
      <span class="close" />
    </div>
  {/each}
  <div class="dump">{dump}</div>
</div>
