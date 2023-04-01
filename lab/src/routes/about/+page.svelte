<script>
    let impressions = 0;
    let likes = 0;
    let engagementRate = 0;
    let averageEngagementRate = 0;
    let percentageDifference = 0;
  
    const options = [
  
      { label: 'Organic', value: 0.5 },
      { label: 'Paid', value: 0.5 },
      { label: 'MDP', value: 1.2 },
      
    ];
  
    function calculateEngagementRate() {
      engagementRate = ((likes / impressions) * 100).toFixed(2);
      calculatePercentageDifference();
    }
  
    function calculatePercentageDifference() {
      percentageDifference = ((engagementRate - averageEngagementRate) / averageEngagementRate) * 100;
      percentageDifference = isNaN(percentageDifference) ? 0 : percentageDifference.toFixed(2);
    }
  </script>
  
  
  
  <main>
    <h2>Calculate engagement rate</h2>
  
    <!-- <div>
      <label for="average-engagement-rate">1. Select social channel</label>
      <select id="average-engagement-rate" bind:value={averageEngagementRate} on:change={calculatePercentageDifference}>
        {#each options as option}
        <option value={option.value}>{option.label}</option>
        {/each}
      </select>
    </div> -->
  
    <div>
      <label for="average-engagement-rate">1. Select social channel</label>
      <select id="average-engagement-rate" bind:value={averageEngagementRate} on:change={calculatePercentageDifference}>
        {#each options as option}
          <option value={option.value}>{option.label} {option.value}</option>
        {/each}
      </select>
    </div>
  
    <div>
      <label for="impressions">2. Add Impressions:</label>
      <input type="number" id="impressions" bind:value={impressions} on:input={calculateEngagementRate} />
    </div>
  
    <div>
      <label for="likes">3. Add social actions:</label>
      <input type="number" id="likes" bind:value={likes} on:input={calculateEngagementRate} />
    </div>
  
    {#if percentageDifference !== NaN}
    <p>Engagement rate: {engagementRate}% ({percentageDifference > 0 ? '+' : ''}{percentageDifference}%)</p>
    {/if}
  </main>
  