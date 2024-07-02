<script>
  // import {createEventDispatcher} from 'svelte';
  import { FeedbackStore } from "../stores";
  import Card from "./Card.svelte";
  export let item;

  // const dispatch = createEventDispatcher();

  const handleDelete = (itemId) => {
    FeedbackStore.update(currentFeedback => currentFeedback.filter(item => item.id !== itemId));
    // dispatch("delete-feedback", itemId);
  };
</script>

<Card>
  <div class="num-display">
    <span>{item.rating}</span>
  </div>
  <div class="close" on:click={() => handleDelete(item.id)}>x</div>
  <div class="text-display">
    {item.text}
  </div>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -1rem;
    left: -1rem;
    width: 2.5rem;
    height: 2.5rem;
    font-size: 1rem;
    font-weight: bold;
    background: #ff6a95;
    color: white;
    border: 1px solid #eee;
    border-radius: 50%;
    padding: 0.5rem;
    text-align: center;
  }

  .close {
    position: absolute;
    top: 0.5rem;
    right: 0.5rem;
    padding: 0.5rem;
    cursor: pointer;
    width: 2.5rem;
    text-align: center;
  }
</style>
