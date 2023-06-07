<script>
    export let style= 'primary';
    export let type='button';
    export let disabled= true;
</script>

<button disabled={disabled} on:cl class="my-button">
    <slot></slot>
</button>

<style>
  .my-button {
    background-color: #4caf50;
    border: none;
    color: white;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    border-radius: 6px;
  }

  .my-button:hover {
    background-color: #45a049;
  }

  .my-button:disabled {
    background-color: gray;
    cursor: not-allowed;
  }
</style>
