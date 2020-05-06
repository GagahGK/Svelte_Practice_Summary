<!-- Buttons.svelte -->
<script>
    import {createEventDispatcher} from 'svelte'
    const dispatch=createEventDispatcher();
    // here we import "createEventDispatcher" class ?, let's call it class  from the svelte library to dispatch = sends data = kirim data.
    // https://svelte.dev/docs#createEventDispatcher
</script>

<!-- This is your View -->
<button on:click={()=> dispatch('NamaEventDiMainApp',true)}>
True
</button>
<!-- dispatchers are functions that can take two arguments: name and detail. 
name untuk nama event yang harus sama dengan di "main" dan detail untuk value-->
<button on:click={()=> dispatch('NamaEventDiMainApp',false)}>
False
</button>