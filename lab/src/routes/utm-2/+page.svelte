<script>
  let url = "";
  let labchannel = "";
  let labgeo = "";
  let campaign = "";
  let utmCode = "";

  function generateUTMCode() {
    if (url && labchannel && labgeo && campaign) {
      utmCode = `${url}${labchannel}${labgeo}&utm_content=lab-2023_${campaign}`.toLowerCase();
    } else {
      utmCode = "";
    }
  }

  function copyUTMCode() {
    let copyText = document.getElementById("utmCodeField");
    copyText.select();
    document.execCommand("copy");
  }
</script>

<style>
  #utmCodeField {
    word-wrap: break-word;
    width: 100%;
  }
</style>

<main>
  <h2>LAB UTM Generator</h2>

  <form on:input={generateUTMCode}>
    <label>
      URL
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
      Geotarget
      <select bind:value={labgeo}>
        <option value="">Select</option>
        <option value="&utm_geo=lab">LAB</option>
        <option value="&utm_geo=lon">United Kingdom</option>
        <option value="&utm_geo=ams">Netherlands</option>
        <option value="&utm_geo=bru">Belgium</option>
      </select>
    </label>

    <label>
      Campaign
      <input type="text" bind:value={campaign}/>
    </label>

  </form>

  {#if utmCode}
    <label>
      Generated UTM Code
      <textarea id="utmCodeField" rows="1" readonly>{utmCode}</textarea>
      <button on:click={copyUTMCode}>Copy UTM Code</button>
    </label>
  {/if}

</main>