<script>
  import {createEventDispatcher} from "svelte";
  export let value;
  export let id;
  export let rating;
  const dispatcher = createEventDispatcher();
  const handleChange = e => {
    dispatcher("ratingSelect", e.target.innerHTML);
  };
</script>

<input
  type="radio"
  checked={rating === id}
  on:change={handleChange}
  name="rating"
  value={rating}
  {id}
/>
<label class="{value==rating ?"selected" : ''}" on:click={handleChange}>{value}</label>

<!-- <h1>{selected}</h1> -->

<style>
  input {
    position: fixed;
    opacity: 0;
    pointer-events: none;
  }
  .selected {
    background: #ff6a95;
  }

  label {
    width: 50px;
    height: 50px;
    background: #fff;
    color: #000;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 15px;
    text-align: center;
    font-size: 15px;
    cursor: pointer;
  }
</style>
