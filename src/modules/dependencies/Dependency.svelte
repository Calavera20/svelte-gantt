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
    <Arrow startX={fromTask.left + 0.9*fromTask.width} startY={fromTask.top } endX={toTask.left + 0.1*toTask.width}
        endY={toTask.top  } {stroke} {strokeWidth} />
</div>

<style>
    .sg-dependency {
        position: absolute;
        width: 100%;
        height: 100%;
    }
</style>