<script>
    import {createEventDispatcher} from 'svelte';
    let dispatch = createEventDispatcher();
    export let reactbutton; //samain sama yang di main sama di pass ke button
</script>


<!-- View -->
{#each reactbutton as IterStory}
    <button on:click={()=>dispatch('emojireactive',{value:IterStory.value})}>
    {IterStory.text}
    </button>
{/each}