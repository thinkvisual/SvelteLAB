<script>
  let url = "";
  let labchannel = "";
  let labgeo = "";
  let utmCode = "";

  function generateUTMCode() {
    utmCode = `${url}${labchannel}${labgeo}&utm_content=lab-2023`;
  }
</script>

<style>
  p {
  word-wrap: break-word;
}
</style>

<main>
  <h2>LAB Marketing UTM Generator</h2>

  <form on:submit|preventDefault={generateUTMCode}>
    <label>
      Add URL
      <input type="text" bind:value={url} />
    </label>


    <label>
      Select location
      <select bind:value={labgeo}>
        <option value="">Select</option>
        <option value="&utm_geo=lab">LAB</option>
        <option value="&utm_geo=lon">United Kingdom</option>
        <option value="&utm_geo=ams">Netherlands</option>
        <option value="&utm_geo=bru">Belgium</option>
      </select>
    </label>


    <label>
      Select Channel
      <select bind:value={labchannel}>
        <option value="">Select</option>
        <option value="?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=organic">LinkedIn | Organic</option>
        <option value="?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=paid">LinkedIn | Paid</option>
        <option value="?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=mdp">LinkedIn | MDP</option>
      </select>
    </label>




    <button type="submit">Generate UTM Code</button>
  </form>

  {#if utmCode}
    <p>{utmCode}</p>
  {/if}
</main>

