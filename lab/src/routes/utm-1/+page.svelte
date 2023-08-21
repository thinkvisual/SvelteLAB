<script>
  // Hardcoded values
  let title = "Custom Open Graph Title";
  let description = "This is a custom description for the Open Graph card.";
  let imageUrl = "/images/test-1.png"; 
  let targetUrl = "https://careers.bcg.com/c/consulting-jobs";

  // Immediate redirect
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

