<script>
  import { onMount } from "svelte";
  export let options = [];
  export let selectedOption = {};

  onMount(async () => {
    options.forEach(option => {
      if (option.active === true) {
        option.active = true;
        selectedOption = option;
      }
    });
  });

  function setToActive(optionToActivate) {
    options.forEach(option => {
      if (option.label === optionToActivate.label) {
        option.active = true;
        selectedOption = optionToActivate;
      } else if (option.active === true) {
        option.active = false;
      }
    });

    options = options;
  }
</script>

<style>
  #segmented {
    height: 29px;
    min-height: 29px;
    border-width: 1px;
    border-color: rgb(33, 150, 243);
    border-radius: 4px;
    border-style: solid;
    display: flex;
    justify-content: stretch;
    -moz-box-align: stretch;
    align-items: stretch;
    margin: 0px 16px 16px;
  }

  .option {
    color: rgb(33, 150, 243);
    background-color: transparent;
    -moz-box-flex: 1;
    flex-grow: 1;
    flex-shrink: 1;
    line-height: normal;
    text-align: center;
    width: 1px;
    min-width: 1px;
    font-size: 14px;
    letter-spacing: -0.006em;
    text-transform: lowercase;
    font-variant: small-caps;
    display: flex;
    -moz-box-pack: center;
    justify-content: center;
    -moz-box-align: center;
    align-items: center;
    transition: background-color 0.2s ease 0s, color 0.2s ease 0s;
  }

  .active {
    color: rgba(255, 255, 255, 0.976);
    background-color: rgb(33, 150, 243);
  }
</style>

<div id="segmented">
  {#each options as option}
    <div
      class="option {option.active ? 'active' : ''}"
      on:click={setToActive(option)}>
      {option.label}
    </div>
  {/each}
</div>
