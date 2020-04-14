<script>
  import VirtualList from "@sveltejs/svelte-virtual-list";
  export let name;
  let selectedOption;

  let options = [
    {
      label: "Left Selection",
      active: true,
      image:
        "https://images.unsplash.com/photo-1518057111178-44a106bad636?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80",
      author: {
        name: "Clay Banks",
        link: "https://unsplash.com/@claybanks"
      }
    },
    {
      label: "Middle Selection",
      image:
        "https://images.unsplash.com/photo-1511920170033-f8396924c348?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80",
      author: {
        name: "Nathan Dumlao",
        link: "https://unsplash.com/@nate_dumlao"
      }
    },
    {
      label: "Right Selection",
      image:
        "https://images.unsplash.com/photo-1581701663554-291c6c9e56d2?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=676&q=80",
      author: {
        name: "Shotlist",
        link: "https://unsplash.com/@shotlist"
      }
    }
  ];

  import SegmentedControl from "./core/ios/SegmentedControl.svelte";
  import SearchBar from "./core/ios/SearchBar.svelte";
  import Card from "./core/common/Card.svelte";
  import UnsplashAttribution from "./misc/UnsplashAtribution.svelte";
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

  <SegmentedControl bind:selectedOption bind:options />

  <div style="column-count:3">
    {#each options as option}
      <div style="display:flex; flex-direction: column">
        {#if option.active === true}
          <Card
            imageSrc={option.image}
            header={option.label}
            title={option.label}
            subtitle={option.label} />
        {:else}
          <div style="background-color: #d4d4d4; padding: 2rem">
            <Card
              imageSrc={option.image}
              header={option.label}
              title={option.label}
              subtitle={option.label} />
          </div>
        {/if}
        <div style="padding-top: 2rem">
          <UnsplashAttribution
            author={option.author.name}
            link={option.author.link} />
        </div>
      </div>
    {/each}
  </div>

  <h1>Scrollable List</h1>
  <div style="margin: 2rem auto; padding: 1rem; width: 400px; border: 1px solid #f3f3f3">
    <SearchBar />
    <VirtualList items={options} height="500px" let:item>
      <div style="padding: 1rem">
        <Card
          imageSrc={item.image}
          header={item.label}
          title={item.label}
          subtitle={item.label} />
      </div>
    </VirtualList>
  </div>
</main>
