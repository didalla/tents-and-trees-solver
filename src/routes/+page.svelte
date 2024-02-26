<script>
    import Field from "$lib/components/Field.svelte";
    import {FieldState} from "$lib/fieldStates.ts";

    let fieldSize = $state({width: 4, height: 4})

    let rowNumbers = $state(Array(fieldSize.height).fill(0));
    let columnNumbers = $state(Array(fieldSize.width).fill(0));
    let fields = $state(Array(fieldSize.height * fieldSize.width).fill(FieldState.empty));
</script>

<main class="h-screen w-screen flex justify-center content-center flex-col space-y-4">
    <h1 class="text-4xl font-bold self-center">
        Zelte und Bäume
    </h1>
    <div class="flex justify-center space-x-4">
        <h3>Field Size</h3>
        <label>
            Width
            <input type="number" bind:value={fieldSize.width} class="w-16"/>
        </label>
        <label>
            Height
            <input type="number" bind:value={fieldSize.height} class="w-16"/>
        </label>
    </div>
    <div
            class="grid-cols-4 grid gap-2 self-center"
            style="grid-template-columns: repeat({fieldSize.width}, minmax(0, 1fr));"
    >
        {#each Array(fieldSize.width * fieldSize.height).fill(0) as _, i}
            <Field bind:state={fields} index={i}/>
        {/each}
    </div>
</main>
