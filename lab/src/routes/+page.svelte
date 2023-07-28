<script>
  let url = "";
  let labchannel = "";
  let labgeo = "";
  let campaign = "";
  let utmCode = "";
  let customField = ""; 
  let isUTMGenerated = false;
  let isCopied = false;
  let team = ""; // Added team variable

  const labchannelOptions = {
    organic: { value: "?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=organic", requiresGeo: true },
    paid: { value: "?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=paid", requiresGeo: true },
    mdp: { value: "?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=mdp", requiresGeo: false }
  };

  function generateUTMCode() {
    const channelOption = labchannelOptions[labchannel];
    const geo = channelOption && channelOption.requiresGeo ? labgeo : '';
    utmCode = `${url}${channelOption.value}${geo}&utm_content=lab-2023_${team}_${campaign}${labchannel === 'mdp' ? `_${customField}` : ''}`; // Added team to the end
    isUTMGenerated = true;
  }

  async function copyToClipboard() {
    await navigator.clipboard.writeText(utmCode);
    isCopied = true;
    setTimeout(() => isCopied = false, 1500); // Reset after 3 seconds
  }

  function resetGenerator() {
    url = "";
    labchannel = "";
    labgeo = "";
    campaign = "";
    utmCode = "";
    customField = ""; 
    team = ""; // Reset team
    isUTMGenerated = false;
  }


</script>

<style>
  p {
    word-wrap: break-word;
    text-transform: lowercase;
  }
  
  .btn {
    padding: 10px 20px;
    background-color: #ececec;
    color: rgb(21, 21, 21);
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .btn:hover {
    background-color: #ececec;
  }
  
  .reset-button {
    background: none;
    border: none;
    color: blue;
    text-decoration: underline;
    cursor: pointer;
    padding: 0;
  }

  </style>

<main>
<h2>LAB UTM Generator</h2>

<form on:submit|preventDefault={generateUTMCode}>
  <label>
    Add URL
    <input type="text" bind:value={url} />
  </label>

  <label> <!-- The new drop-down menu -->
    Team
    <select bind:value={team}>
      <option value="" disabled selected hidden>Select</option>
      <option value="S1">Climate</option>
      <option value="S2">DT AI</option>
      <option value="S3">Centre</option>
      <option value="S4">CC&P</option>
      <option value="S5">Alumni</option>
      <option value="S6">Resilience</option>
    </select>
  </label>

  <label>
    Channel
    <select bind:value={labchannel}>
      <option value="" disabled selected hidden>Select</option>
      <option value="organic">LinkedIn | Organic</option>
      <option value="paid">LinkedIn | Paid</option>
      <option value="mdp">LinkedIn | MDP</option>
    </select>
  </label>

  {#if labchannel && labchannelOptions[labchannel].requiresGeo}
    <label>
      Location
      <select bind:value={labgeo}>
        <option value="" disabled selected hidden>Select</option>
        <option value="&utm_geo=lab">LAB</option>
        <option value="&utm_geo=lon">United Kingdom</option>
        <option value="&utm_geo=ams">Netherlands</option>
        <option value="&utm_geo=bru">Belgium</option>
      </select>
    </label>
  {:else if labchannel === 'mdp'}
    <label>
      MDP
      <input type="text" bind:value={customField}/>
    </label>
  {/if}

  {#if labchannel}
    <label>
      Campaign
      <input type="text" bind:value={campaign}/>
    </label>

    {#if !isUTMGenerated}
      <button class="btn" type="submit">Generate link</button>
    {:else}
      <button class="btn" type="button" on:click={copyToClipboard}>{isCopied ? 'Link copied!' : 'Copy link'}</button>
    {/if}
  {/if}
</form>

{#if utmCode}
  <p>{utmCode}</p>
{/if}

{#if isUTMGenerated}
  <button class="reset-button" type="button" on:click={resetGenerator}>Reset</button>
{/if}
</main>
