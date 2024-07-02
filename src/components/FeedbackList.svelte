<script>
  // import { onMount, onDestroy } from "svelte";
  import { FeedbackStore } from "../stores";
  import { fade, scale } from "svelte/transition";
  import FeedbackItem from "./FeedbackItem.svelte";
  // let feedback = []; // set empty array just in case, but it should be the one that was passed down
  
  // let unsubscribe = FeedbackStore.subscribe(data => feedback = data); // subscribe to the store
  // // onMount(() => console.log('mounted'))
  // // onDestroy(() => unsubscribe())
</script>

{#each $FeedbackStore as fb (fb.id)} <!-- $ to access the store and unsub in shorthand -->
  <div in:scale out:fade={{ duration: 500 }}>
    <FeedbackItem item={fb} />
    <!-- <FeedbackItem item={fb} on:delete-feedback /> -->
    <!-- event forwarding up to parent with the custom event thing, no longer needed because using stores now -->
  </div>
{/each}
