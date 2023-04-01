<script>
  // export let options1 = ['Option 1A', 'Option 1B', 'Option 1C'];
  export let options2 = ['Option 2A', 'Option 2B', 'Option 2C'];
  export let options3 = ['Option 3A', 'Option 3B', 'Option 3C'];
  let selected1 = '';
  let selected2 = '';
  let selected3 = '';

  function handleInput(event) {
    selected1 = event.target.value;
  }

  function handleSelect2(event) {
    selected2 = event.target.value;
  }

  function handleSelect3(event) {
    selected3 = event.target.value;
  }
</script>

<main>
  <h2>Generate UTM</h2>

  <div class="dropdown">
    <label for="input1">Input 1:</label>
    <input type="text" id="input1" on:input={handleInput}>
  </div>

  <div class="dropdown">
    <label for="dropdown2">Dropdown 2:</label>
    <select id="dropdown2" on:change={handleSelect2}>
      {#each options2 as option}
        <option value={option}>{option}</option>
      {/each}
    </select>
  </div>

  <div class="dropdown">
    <label for="dropdown3">Dropdown 3:</label>
    <select id="dropdown3" on:change={handleSelect3}>
      {#each options3 as option}
        <option value={option}>{option}</option>
      {/each}
    </select>
  </div>

  <div class="selected-options">
    <p>UTM</p>
    <p>{selected1}{selected2}{selected3}</p>
  </div>
</main>
