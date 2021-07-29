

<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    export let text = '';
    const submit = () => dispatch('submit');
</script>


<textarea rows="25" cols="25" bind:value={text}></textarea>
<button on:click={submit}>Submit</button>