<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch=createEventDispatcher();
    export let emojis; //harus sama kyk yang di main, ini data yang mau di oper oper nya
</script>
<!-- View -->
{#each emojis as tombol}
<button on:click={()=>dispatch('clickEmoji',{value:tombol.value})}>
    {tombol.expression}
</button>
<!-- ({value:var.value}) atau (var.value)emoji-->
<!-- kalau ({value:var.value}) di main jadi namafun.detail.value-->
{/each}
