<script>
  let url = "";
  let utm_source = "";
  let utm_medium = "";
  let utm_campaign = "";
  let utm_term = "";
  let utm_content = "";
  let utmCode = "";

  function generateUTMCode() {
    utmCode = `${url}?utm_source=${utm_source}&utm_medium=${utm_medium}&utm_campaign=${utm_campaign}&utm_term=${utm_term}&utm_content=${utm_content}`;
  }
</script>

<style>
  /* Add your styles here */
</style>

<main>
  <h2>LAB Marketing UTM Generator</h2>

  <form on:submit|preventDefault={generateUTMCode}>
    <label>
      URL:
      <input type="text" bind:value={url} />
    </label>

    <label>
      Source:
      <select bind:value={utm_source}>
        <option value="">Select source</option>
        <option value="google">Google</option>
        <option value="facebook">Facebook</option>
        <option value="twitter">Twitter</option>
      </select>
    </label>

    <label>
      Medium:
      <select bind:value={utm_medium}>
        <option value="">Select medium</option>
        <option value="cpc">CPC</option>
        <option value="banner">Banner</option>
        <option value="email">Email</option>
      </select>
    </label>

    <label>
      Campaign:
      <select bind:value={utm_campaign}>
        <option value="">Select campaign</option>
        <option value="spring_sale">Spring Sale</option>
        <option value="summer_promo">Summer Promo</option>
        <option value="fall_discount">Fall Discount</option>
      </select>
    </label>

    <label>
      Term:
      <select bind:value={utm_term}>
        <option value="">Select term</option>
        <option value="running_shoes">Running Shoes</option>
        <option value="soccer_jerseys">Soccer Jerseys</option>
        <option value="baseball_caps">Baseball Caps</option>
      </select>
    </label>

    <label>
      Content:
      <select bind:value={utm_content}>
        <option value="">Select content</option>
        <option value="ad_a">Ad A</option>
        <option value="ad_b">Ad B</option>
        <option value="ad_c">Ad C</option>
      </select>
    </label>

    <button type="submit">Generate UTM Code</button>
  </form>

  {#if utmCode}
    <p>{utmCode}</p>
  {/if}
</main>

