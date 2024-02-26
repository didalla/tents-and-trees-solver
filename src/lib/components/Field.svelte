<script lang="ts">

    import {FieldState} from "$lib/fieldStates";

    export let state = Array(0).fill(FieldState.empty);
    export let index: number = 0;

    const handleClick = () => {
        console.log(index, state[index])

        if (state[index] === FieldState.empty) {
            state[index] = FieldState.tree;
        } else {
            state[index] = FieldState.empty;
        }
    }
</script>

<button class="h-10 hover:scale-105 hover:shadow transition-all aspect-square rounded-md {state[index] === FieldState.empty ? 'bg-neutral-500' : ''} {state[index] === FieldState.tree ? 'bg-green-600' : ''} {state[index] === FieldState.tent ? 'bg-orange-600' : ''}"
     on:click={() => handleClick()}
>
</button>