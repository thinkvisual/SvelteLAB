<script>
  export let prefix = '';
  
  function generateRandomNumber() {
    const min = 1e7;
    const max = 1e8 - 1;
    const randomNumber = Math.floor(Math.random() * (max - min + 1)) + min;
    return `${prefix}${randomNumber}`;
  }
  
  let randomNumber = generateRandomNumber();
  
  function copyToClipboard() {
    navigator.clipboard.writeText(randomNumber);
  }
</script>

<main>
<h2>Generate random number</h2>
<p>The random number is: {randomNumber}</p>
<button on:click={copyToClipboard}>
  Copy to Clipboard
</button>
</main>