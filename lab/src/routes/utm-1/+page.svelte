<script>
  let title = "Custom Open Graph Title";
  let description = "This is a custom description for the Open Graph card.";
  let imageUrl = "/images/test-1.png"; // replace with your image URL
  let targetUrl = "https://careers.bcg.com/c/consulting-jobs"; // replace with your target URL
</script>

<svelte:head>
  <meta property="og:title" content={title} />
  <meta property="og:description" content={description} />
  <meta property="og:image" content={imageUrl} />
  <meta property="og:url" content={targetUrl} />
</svelte:head>

<a href={targetUrl}>
  <img src={imageUrl} alt={title} width="300" />
  <h2>{title}</h2>
  <p>{description}</p>
</a>

