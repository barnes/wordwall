<script>
    export let word;
    export let font;
    export let size;
</script>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Gowun+Batang:wght@700&family=Inter:wght@600&family=Style+Script&display=swap" rel="stylesheet"> 
</svelte:head>

<h1 style="--font: {font}">{word}</h1>

<style>
    h1 {
        font-size: 2in;
        font-family: var(--font);
    }
</style>