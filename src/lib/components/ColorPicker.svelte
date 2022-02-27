<script>
    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher();
    export let color;
    export let size;
</script>

<button class="picker" on:click={()=>{dispatch('click',{})}} style:background-color="{color}" style:height="{size}px" style:width="{size}px"></button>

<style>
    .picker{
        border-radius:50%;
        border:none;
    }

    .picker:hover{
        cursor:pointer;
        filter: brightness(0.8);
    }
</style>

