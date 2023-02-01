<script>
    export let left = Math.random() * (innerWidth - 300);
    export let top = Math.random() * (innerHeight - 300);

    let moving = false;

    function onMouseDown () {
        moving = true;
    }

    function onMouseMove(e){
        if(moving){
            left += e.movementX;
            top += e.movementY;
        }
    }

    function onMouseUp(){
        moving = false;
    }

</script>

<section on:mousedown={onMouseDown} style="left:{left}px; top:{top}px;" class="draggable">
<slot></slot>
</section>

<svelte:window on:mousemove={onMouseMove} on:mouseup={onMouseUp} />

<style>
    .draggable {
        user-select: none;
        cursor: move;
        position: absolute;
    }
</style>