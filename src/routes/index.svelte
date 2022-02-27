<script>
    import Picker from '$lib/Picker.svelte';

    function handleColorChanged(e){
        console.log('color changed', e.detail);
    }
</script>

<Picker on:colorChanged={handleColorChanged}/>