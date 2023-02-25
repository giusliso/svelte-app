<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    export let inputValue = 'empty'
    const dispatch = createEventDispatcher();
    let value = ''
    export let disableX

    // logic goes here
    let foo = 'bottone'
    let x = 0;
    let y = 0;
    let lista: any[] = [1,2,3]

    function add() {

        if(value){
            lista = [...lista, ...value[0]]
            dispatch('pippo', value)
        }


    }
    function sumTotal(value){
        return  value + y;
    }
    function reset(){
        y = 0;
        x = 0;
    }

    $: total = x + y

</script>
Input value is : {inputValue}
<br /><br />

<button on:click={() => x += 1} disabled = {disableX}>{foo}</button>
x:{x}
<br /><br />
<button on:click={() => y += 2}>{foo}</button>
y:{y}
<br /><br />
<button on:click={() => {reset()}}>RESET</button>

<br /><br />
total: {total}
<br /><br /><br />
{#if total === 1}
     <p>Totale uno</p>
{:else if total > 1 }
    totale maggiore di 1
{:else}
    totale zero
{/if}

<input name="pippo" bind:value = {value} ><button on:click={() => add()} > ADD</button>

{#each lista as v, i}
    <li>{v} :id {i} </li>
{/each}
<style>
    :global(body) {
        font-size: x-large;
    }
    /* styles go here */
    button {
        font-size: x-large;
        background-color: darkgrey;
    }
</style>
