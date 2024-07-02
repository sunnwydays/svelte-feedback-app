<script>
  import { v4 as uuidv4 } from "uuid";
  // import { createEventDispatcher } from "svelte";
  import { FeedbackStore } from "../stores";
  import { slide } from "svelte/transition";
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  import RatingSelect from "./RatingSelect.svelte";

  // const dispatch = createEventDispatcher();

  let text = "";
  let rating = "";
  let disabled = true;
  let message = "";
  let min = 10;

  let feedback = [];

  $: {  // reactive statement
    if (text == "") {
        message = "";
    } else if (text.trim().length <= min) {
      message = `Please enter at least ${min} characters`;
    } else if (!rating) {
      message = "Please select a rating";
    } else {
      message = "";
    }
    disabled = text.trim().length <= min || !rating;
  };

  const handleSelect = (e) => (rating = e.detail);

  const handleSubmit = () => {
    // redundant check that the text is at least 10 characters long in case someone goes into devtools to enable the button
    if (text.trim().length > min && rating) {
      const newFeedback = {
        id: uuidv4(),
        text,
        rating: +rating,
      }; //plus sign to convert to number

      message = "Thank you for your feedback!";
      // dispatch("add-feedback", newFeedback); // dispatch needed to notify parent component of change
      FeedbackStore.update(currentFeedback => [newFeedback, ...currentFeedback]);
      text = "";
    //   rating = ""  if you wanted to do this 
      setTimeout(() => {
        message = "";
      }, 3000);
    }
  };
</script>

<Card>
  <header>
    <h2>Rate your service today</h2>
  </header>
  <form on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:rating-select={handleSelect} />
    <div class="input-group">
      <input
        type="text"
        bind:value={text}
        placeholder="Enter your feedback"
      />
      <Button type="submit" {disabled}>Submit</Button>
    </div>
    {#if message}
      <div class="message" out:slide >{message}</div>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
