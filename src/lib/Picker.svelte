<script>
    import {onMount, createEventDispatcher} from 'svelte';
    import ColorCircle from '$lib/components/ColorCircle.svelte';
    import ColorPicker from '$lib/components/ColorPicker.svelte';
    const dispatch = createEventDispatcher();

    export let palette = {
        // black: "#000000",
        // white: "#ffffff",
        red: { 50: "#ffebee", 100: "#ffcdd2", 200: "#ef9a9a", 300: "#e57373", 400: "#ef5350", 500: "#f44336", 600: "#e53935", 700: "#d32f2f", 800: "#c62828", 900: "#b71c1c" },
        pink: { 50: "#fce4ec", 100: "#f8bbd0", 200: "#f48fb1", 300: "#f06292", 400: "#ec407a", 500: "#e91e63", 600: "#d81b60", 700: "#c2185b", 800: "#ad1457", 900: "#880e4f" },
        purple: { 50: "#f3e5f5", 100: "#e1bee7", 200: "#ce93d8", 300: "#ba68c8", 400: "#ab47bc", 500: "#9c27b0", 600: "#8e24aa", 700: "#7b1fa2", 800: "#6a1b9a", 900: "#4a148c" },
        deepPurple: { 50: "#ede7f6", 100: "#d1c4e9", 200: "#b39ddb", 300: "#9575cd", 400: "#7e57c2", 500: "#673ab7", 600: "#5e35b1", 700: "#512da8", 800: "#4527a0", 900: "#311b92" },
        indigo: { 50: "#e8eaf6", 100: "#c5cae9", 200: "#9fa8da", 300: "#7986cb", 400: "#5c6bc0", 500: "#3f51b5", 600: "#3949ab", 700: "#303f9f", 800: "#283593", 900: "#1a237e" },
        blue: { 50: "#e3f2fd", 100: "#bbdefb", 200: "#90caf9", 300: "#64b5f6", 400: "#42a5f5", 500: "#2196f3", 600: "#1e88e5", 700: "#1976d2", 800: "#1565c0", 900: "#0d47a1" },
        lightBlue: { 50: "#e1f5fe", 100: "#b3e5fc", 200: "#81d4fa", 300: "#4fc3f7", 400: "#29b6f6", 500: "#03a9f4", 600: "#039be5", 700: "#0288d1", 800: "#0277bd", 900: "#01579b" },
        cyan: { 50: "#e0f7fa", 100: "#b2ebf2", 200: "#80deea", 300: "#4dd0e1", 400: "#26c6da", 500: "#00bcd4", 600: "#00acc1", 700: "#0097a7", 800: "#00838f", 900: "#006064" },
        teal: { 50: "#e0f2f1", 100: "#b2dfdb", 200: "#80cbc4", 300: "#4db6ac", 400: "#26a69a", 500: "#009688", 600: "#00897b", 700: "#00796b", 800: "#00695c", 900: "#004d40" },
        green: { 50: "#e8f5e9", 100: "#c8e6c9", 200: "#a5d6a7", 300: "#81c784", 400: "#66bb6a", 500: "#4caf50", 600: "#43a047", 700: "#388e3c", 800: "#2e7d32", 900: "#1b5e20" },
        lightGreen: { 50: "#f1f8e9", 100: "#dcedc8", 200: "#c5e1a5", 300: "#aed581", 400: "#9ccc65", 500: "#8bc34a", 600: "#7cb342", 700: "#689f38", 800: "#558b2f", 900: "#33691e" },
        lime: { 50: "#f9fbe7", 100: "#f0f4c3", 200: "#e6ee9c", 300: "#dce775", 400: "#d4e157", 500: "#cddc39", 600: "#c0ca33", 700: "#afb42b", 800: "#9e9d24", 900: "#827717" },
        yellow: { 50: "#fffde7", 100: "#fff9c4", 200: "#fff59d", 300: "#fff176", 400: "#ffee58", 500: "#ffeb3b", 600: "#fdd835", 700: "#fbc02d", 800: "#f9a825", 900: "#f57f17" },
        amber: { 50: "#fff8e1", 100: "#ffecb3", 200: "#ffe082", 300: "#ffd54f", 400: "#ffca28", 500: "#ffc107", 600: "#ffb300", 700: "#ffa000", 800: "#ff8f00", 900: "#ff6f00" },
        orange: { 50: "#fff3e0", 100: "#ffe0b2", 200: "#ffcc80", 300: "#ffb74d", 400: "#ffa726", 500: "#ff9800", 600: "#fb8c00", 700: "#f57c00", 800: "#ef6c00", 900: "#e65100" },
        deepOrange: { 50: "#fbe9e7", 100: "#ffccbc", 200: "#ffab91", 300: "#ff8a65", 400: "#ff7043", 500: "#ff5722", 600: "#f4511e", 700: "#e64a19", 800: "#d84315", 900: "#bf360c" },
        brown: { 50: "#efebe9", 100: "#d7ccc8", 200: "#bcaaa4", 300: "#a1887f", 400: "#8d6e63", 500: "#795548", 600: "#6d4c41", 700: "#5d4037", 800: "#4e342e", 900: "#3e2723" },
        grey: { 50: "#fafafa", 100: "#f5f5f5", 200: "#eeeeee", 300: "#e0e0e0", 400: "#bdbdbd", 500: "#9e9e9e", 600: "#757575", 700: "#616161", 800: "#424242", 900: "#212121" },
        blueGrey: { 50: "#eceff1", 100: "#cfd8dc", 200: "#b0bec5", 300: "#90a4ae", 400: "#78909c", 500: "#607d8b", 600: "#546e7a", 700: "#455a64", 800: "#37474f", 900: "#263238" },
    }

    export let margin              = 1; // colorsMargin : distance between colors
    export let size                = 50; // colorSize    : size of circle
    export let colorsPerRow        = 6; // colorsPerRow : numbero of colors per row
    export let defaultTint         = 500; // defaultTint  : base tint
    export let useSpectrumPicker   = true; // useSpectrumPicker
    export let mode                = 'palette'; // button vs palette
    export let selectedColor       = palette['red'][defaultTint]; // value : color selected (#000000)
    let colorsName          = Object.keys(palette);
    let colorSpectrum = [];
    let bool_show           = false; 
    let widthPicker         = 0;
    let showSpectrum        = false;
    let selectedColorName = 'red';

    $ : updateWidthPicker(colorsPerRow, margin, size);

    function updateWidthPicker(p, m, s){
        widthPicker = colorsPerRow*(margin*2 + size)+1;
    }

    function handleColorChosen(e){
        const oldSelected = selectedColor;
        selectedColor = e.detail.color;
        bool_show = false;
        dispatch('colorChanged', {old:oldSelected, new:selectedColor});
    }

    function handleSpectrum(e){
        selectedColorName = e.detail.name;
        colorSpectrum = Object.keys(palette[selectedColorName]);
        showSpectrum = true;
    }
</script>

<div class="main-container">
    <div class="colors-container" style:width="{widthPicker}px">
        {#if !bool_show && mode == 'button'}
            <ColorPicker color={selectedColor} {size} on:click={()=>{bool_show = true}} />
        {:else}
            {#if useSpectrumPicker && showSpectrum}
                {#each colorSpectrum as tint}
                    {@const color = palette[selectedColorName][tint]}
                    <ColorCircle {color} {size} {margin} name={selectedColorName} {selectedColor} {useSpectrumPicker} isSpectrumElement={true} on:colorChosen={handleColorChosen} />
                {:else}
                    Pas de spectre de couleur
                {/each}
                <button class="return" on:click={() => {showSpectrum = false}}>
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--! Font Awesome Pro 6.0.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M447.1 256C447.1 273.7 433.7 288 416 288H109.3l105.4 105.4c12.5 12.5 12.5 32.75 0 45.25C208.4 444.9 200.2 448 192 448s-16.38-3.125-22.62-9.375l-160-160c-12.5-12.5-12.5-32.75 0-45.25l160-160c12.5-12.5 32.75-12.5 45.25 0s12.5 32.75 0 45.25L109.3 224H416C433.7 224 447.1 238.3 447.1 256z"/></svg>
                </button>
            {:else}
                {#each colorsName as name}
                    {@const color = palette[name][defaultTint]}
                    <ColorCircle {color} {size} {margin} {name} {selectedColor} {useSpectrumPicker} on:colorChosen={handleColorChosen} on:showSpectrum={handleSpectrum}/>
                {:else}
                    Pas de couleurs
                {/each}
            {/if}

        {/if}
    </div>
</div>

<style>
    .main-container{
        position:relative;
    }
    
    .colors-container{
        display:flex;
        flex-wrap:wrap;
        position:relative;
    }

    .return{
        background:transparent;
        border:transparent;
        width:50px;
        height:50px;
        margin:1px;
        border-radius:50px;
    }

    .return:hover{
        cursor:pointer;
        background:rgba(0,0,0,0.1);
    }
</style>