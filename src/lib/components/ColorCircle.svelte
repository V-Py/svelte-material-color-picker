<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();
    export let color = "#e91e63";
    export let size = 50;
    export let margin = 5;
    export let name = "pink";
    export let selectedColor;
</script>

<div class="circle {selectedColor == color ? 'selected' : ''}" style:background-color="{color}" style:height="{size}px" style:width="{size}px" style:margin="{margin}px" on:click={()=>{dispatch('colorChosen',{name, color})}}>

</div>


<style>

    .circle{
        border-radius:50%;
        border:none;
    }

    .circle:hover{
        cursor:pointer;
        filter: brightness(0.8);
    }

    .selected{
        box-shadow:inset 0px 0px 0px 7px white;
        border:3px solid black;
    }
</style>