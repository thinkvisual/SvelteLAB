<script>
  let url = "";
  let labchannel = "";
  let labgeo = "";
  let campaign = "";
  let utmCode = "";

  function generateUTMCode() {
    utmCode = `${url}${labchannel}${labgeo}&utm_content=lab-2023_${campaign}`;
  }
</script>

<style>
  p {
  word-wrap: break-word;
  text-transform: lowercase;
}
</style>

<main>
  <h2>LAB UTM Generator</h2>

  <form on:submit|preventDefault={generateUTMCode}>
    <label>
      Add URL
      <input type="text" bind:value={url} />
    </label>

    <label>
      Channel
      <select bind:value={labchannel}>
        <option value="">Select</option>
        <option value="?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=organic">LinkedIn | Organic</option>
        <option value="?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=paid">LinkedIn | Paid</option>
        <option value="?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=mdp">LinkedIn | MDP</option>
      </select>
    </label>


    <label>
      Targeting
      <select bind:value={labgeo}>
        <option value="">Select</option>
        <option value="&utm_geo=lab">LAB</option>
        <option value="&utm_geo=lon">United Kingdom</option>
        <option value="&utm_geo=ams">Netherlands</option>
        <option value="&utm_geo=bru">Belgium</option>
      </select>
    </label>

    <label>
      Add campaign
      <input type="text" bind:value={campaign}/>
    </label>

    <button type="submit">Generate UTM Code</button>
  </form>

  {#if utmCode}
    <p>{utmCode}</p>
  {/if}
</main>

