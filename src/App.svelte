<script>
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";
  import FeedbackForm from "./components/FeedbackForm.svelte";

  // $: count = feedback.length;
  // $: average = feedback.length > 0
  //   ? (feedback.reduce((a, { rating }) => a + rating, 0) / feedback.length).toFixed(1)
  //   : '0.0';

//   const addFeedback = (e) => {
//     feedback = [e.detail, ...feedback];
//   };

//   const deleteFeedback = (e) => {
//     const itemId = e.detail;
//     feedback = feedback.filter((item) => item.id !== itemId);
//   };
// </script>

<main class="container">
  <!-- <FeedbackForm on:add-feedback={addFeedback} /> -->
  <FeedbackForm />
  <!-- <FeedbackStats {count} {average} /> -->
  <FeedbackStats />
  <!-- <FeedbackList {feedback} on:delete-feedback={deleteFeedback} /> -->
  <FeedbackList />
</main>


<!-- svelte demo
<script>
	let firstName = 'John';
	let lastName = 'Deere';
	let color = 'green';
	let showText = true;
	let users = [
		{ id: 1, name: 'John' },
		{ id: 2, name: 'Jane' },
		{ id: 3, name: 'Jack' }
	];

	$: name = `${firstName} ${lastName}`; // reactive variable
	// no need for state

	const toggle = () => {
		color = color === 'green' ? 'red' : 'green';
		showText = !showText;
		users = [...users, { id: users.length + 1, name: 'New User' }];
	};
</script>

<main>
	<h1 style="color: {color}">Hello {name}!</h1>
	{#if showText}
		<p>ustoaehisnchoda usnct</p>
	{:else}
		<p>Hidden text</p>
	{/if}
	<button on:click={toggle}>click this button!! 🔘</button>

	{#each users as user (user.id)}
		<h2>{user.id} - {user.name}</h2>
	{/each}
</main> -->
