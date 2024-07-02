<script>
  import { fade, scale } from "svelte/transition";
  import FeedbackItem from "./FeedbackItem.svelte";
  export let feedback = []; // set empty array just in case, but it should be the one that was passed down
</script>

{#each feedback as fb (fb.id)}
  <div in:scale out:fade={{ duration: 500 }}>
    <FeedbackItem item={fb} on:delete-feedback />
    <!-- event forwarding up to parent with the custom event thing -->
  </div>
{/each}
