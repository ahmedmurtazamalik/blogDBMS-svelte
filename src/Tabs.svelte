<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    export let tabs;
    export let activetab;

</script>

<div class="tabs">
    <ul>
        {#each tabs as tab}
            <li on:click={() => dispatch('tabChange',tab)}>
                <div class:active={tab === activetab}> {tab} </div>
            </li>
        {/each}
    </ul>

</div>


<style>
    ul {
        display: flex;
        justify-content: center;
        padding: 0%;  
        list-style-type: none;
    }

    li {
        color: #555;
        cursor: pointer;
        font-size: large;
        font-weight: bold;
        margin-right: 20px;
    }

    .active{
        color:green;
        border-bottom: 2px solid green;
        padding-bottom: 8px;
    }


</style>