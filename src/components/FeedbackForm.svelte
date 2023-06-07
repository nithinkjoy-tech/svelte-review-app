<script>
  import Button from "./Button.svelte";
  import {createEventDispatcher} from "svelte";
  import Radio from "./Radio.svelte";
  export let disabled = true;
  $: review = "";
  $: rating = 0;

  const dispatch = createEventDispatcher();
  const handleSubmit = e => {
    dispatch("addFeedback", {review, rating});
    review = "";
    rating = "";
  };

  const handleInput = () => {
    if (review.length > 5&&rating) {
      disabled = false;
    } else {
      disabled = true;
    }
  };

  const ratingSelect = ({detail}) => {
      rating = detail;
      handleInput()
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <!-- Ratting select -->
  <div class="input-group">
    <h1 style="display:flex;justify-content:center" >How would you rate your service with us</h1>
    <div class="rating-container">
      {#each Array.from([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]) as no}
        <Radio
          on:ratingSelect={ratingSelect}
          {rating}
          value={no}
          id={no}
          name="rating"
        />
      {/each}
    </div>
    <input
      bind:value={review}
      on:input={handleInput}
      class="my-textbox"
      type="text"
      placeholder="tell us review"
    />
    <Button {disabled}>Send</Button>
  </div>
</form>

<style>
  .my-textbox {
    width: 650px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
  }

  .my-textbox:focus {
    outline: none;
    border-color: #4caf50;
    box-shadow: 0 0 5px rgba(76, 175, 80, 0.5);
  }

  .rating-container {
    margin-bottom: 20px;
    display: flex;
    justify-content: space-between;
  }
</style>
