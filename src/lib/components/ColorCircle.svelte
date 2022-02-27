<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();
    export let color;
    export let size;
    export let margin;
    export let name;
    export let selectedColor;
</script>

<div class="circle {selectedColor == color ? 'selected' : ''}" style:background-color="{color}" style:height="{size}px" style:width="{size}px" style:margin="{margin}px" on:click={()=>{dispatch('colorChosen',{name, color})}}>
    <div class="inner-circle {selectedColor == color ? 'selected' : ''}" style:background-color="{color}" style:height="{size/1.4}px" style:width="{size/1.4}px">
    </div>
</div>

<style>
    .circle{
        border-radius:50%;
        border:none;
        position:relative;
        display:flex;
        justify-content: center;
        align-items: center;
    }

    .circle:hover{
        cursor:pointer;
        filter: brightness(0.9);
    }

    .circle.selected{
        box-shadow:inset 0px 0px 0px 7px rgba(0,0,0,0.2);
    }

    .inner-circle.selected{
        box-shadow:inset 0px 0px 0px 5px white;

    }

    .inner-circle{
        border-radius: 50%;
        border:none;
    }
</style>