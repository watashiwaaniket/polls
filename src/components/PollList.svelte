<script>
    // import { onDestroy, onMount } from 'svelte';
    import PollStore from '../store/PollStore.js';
    import PollDetails from "./PollDetails.svelte";
    
    //export let polls = [];

    // const unsub = PollStore.subscribe(data => {
    //     polls = data;
    // });

    // onDestroy(() => {
    //     console.log('components destroyed');
    //     unsub();
    // });


</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div>
            <PollDetails {poll}/>    
        </div>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>