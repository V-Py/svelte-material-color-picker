<script>
    export let color = "#e91e63";
    export let size = 50;
    export let margin = 5;
</script>


<div class="circle" style:background-color="{color}" style:height="{size}px" style:width="{size}px" style:margin="{margin}px"></div>


<style>

    .circle{
        border-radius:50%;
        border:none;
    }

    .circle:hover{
        cursor:pointer;
        filter: brightness(0.8);
    }
</style>