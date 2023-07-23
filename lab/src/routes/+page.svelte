<script>
    let url = "";
    let labchannel = "";
    let labgeo = "";
    let campaign = "";
    let utmCode = "";
    let customField = ""; 
    let isUTMGenerated = false;
  
    const labchannelOptions = {
      organic: { value: "?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=organic", requiresGeo: true },
      paid: { value: "?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=paid", requiresGeo: true },
      mdp: { value: "?utm_source=linkedin&utm_medium=social&utm_campaign=none&utm_description=mdp", requiresGeo: false }
    };
  
    function generateUTMCode() {
      const channelOption = labchannelOptions[labchannel];
      const geo = channelOption && channelOption.requiresGeo ? labgeo : '';
      utmCode = `${url}${channelOption.value}${geo}&utm_content=lab-2023_${campaign}${labchannel === 'mdp' ? `_${customField}` : ''}`;
      isUTMGenerated = true;
    }
  
    async function copyToClipboard() {
      await navigator.clipboard.writeText(utmCode);
    }
  
    function resetGenerator() {
      url = "";
      labchannel = "";
      labgeo = "";
      campaign = "";
      utmCode = "";
      customField = ""; 
      isUTMGenerated = false;
    }
  </script>
  
  <style>
    p {
      word-wrap: break-word;
      text-transform: lowercase;
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
  
      <label>
        Channel
        <select bind:value={labchannel}>
          <option value="">Select</option>
          <option value="organic">LinkedIn | Organic</option>
          <option value="paid">LinkedIn | Paid</option>
          <option value="mdp">LinkedIn | MDP</option>
        </select>
      </label>
  
      {#if labchannel && labchannelOptions[labchannel].requiresGeo}
        <label>
          Location
          <select bind:value={labgeo}>
            <option value="">Select</option>
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
          <button type="submit">Generate UTM Code</button>
        {:else}
          <button type="button" on:click={copyToClipboard}>Copy UTM Code</button>
        {/if}
      {/if}
    </form>
  
    {#if utmCode}
      <p>{utmCode}</p>
    {/if}
  
    {#if isUTMGenerated}
      <button type="button" on:click={resetGenerator} class="reset-button">Reset</button>
    {/if}
  </main>
  