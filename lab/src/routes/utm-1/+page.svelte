<script>
  // Hardcoded values
  let title = "Custom Open Graph Title";
  let description = "This is a custom description for the Open Graph card.";
  let imageUrl = "/images/test-1.png"; // Assuming you have an image in your static/images directory
  let targetUrl = "https://careers.bcg.com/c/consulting-jobs";

  // Redirect to the target URL on page load
  import { onMount } from 'svelte';

  onMount(() => {
    window.location.href = targetUrl;
  });
</script>

<svelte:head>
  <meta property="og:title" content={title} />
  <meta property="og:description" content={description} />
  <meta property="og:image" content={imageUrl} />
</svelte:head>

