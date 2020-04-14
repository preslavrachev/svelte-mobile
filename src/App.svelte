<script>
  export let name;
  let selectedOption;

  import SegmentedControl from "./core/ios/SegmentedControl.svelte";
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h1>Hello {name}!</h1>
  <p>
    Visit the
    <a href="https://svelte.dev/tutorial">Svelte tutorial</a>
    to learn how to build Svelte apps.
  </p>

  <SegmentedControl
    bind:selectedOption
    options={[{ label: 'A', active: true }, { label: 'B' }, { label: 'C' }]} />
  <div style="display:flex">
    {#if selectedOption && selectedOption.label}
      <div>Selected option:</div>
      <div>{selectedOption.label}</div>
    {/if}
  </div>
</main>
