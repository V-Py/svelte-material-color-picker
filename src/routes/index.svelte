<script>
    import Picker from '$lib/Picker.svelte';

    function handleColorChanged(e){
        console.log('color changed', e.detail);
    }

    let colorsPerRow = 6;
    let margin = 1;

</script>
<button on:click={() => {colorsPerRow++}}>peRow{colorsPerRow} </button>
<button on:click={() => {margin++}}>margin{margin} </button>

<Picker on:colorChanged={handleColorChanged} {colorsPerRow} {margin}/>