<script lang="ts">
    import Arrow from './Arrow.svelte';

    import { taskStore } from '../../core/store';

    export let id;
    export let fromId;
    export let toId;
    export let stroke;
    export let strokeWidth;

    let fromTask;
    $: fromTask = $taskStore.entities[fromId];

    let toTask;
    $: toTask = $taskStore.entities[toId];
</script>

<div class="sg-dependency" style="left:0;top:0" data-dependency-id="{id}">
    <Arrow startX={fromTask.left + fromTask.width + (fromTask.width<20? -(fromTask.width/2) :-10) } startY={fromTask.top } endX={toTask.left  + (toTask.width<20? (toTask.width/2) :10)}
        endY={toTask.top  } {stroke} {strokeWidth} />
</div>

<style>
    .sg-dependency {
        position: absolute;
        width: 100%;
        height: 100%;
    }
</style>