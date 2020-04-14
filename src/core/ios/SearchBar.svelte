<script>
  import SearchIcon from "./icons/Search.svelte";
</script>

<style>
  .search {
    padding: 0px 16px 16px;
  }

  .search .input {
    color: rgb(0, 0, 0);
    height: 36px;
    padding: 0px 12px;
    border-radius: 18px;
    background-color: rgba(0, 0, 0, 0.05);
    display: flex;
    -moz-box-align: center;
    align-items: center;
  }

  .search .input :global(svg) {
    fill: rgb(153, 153, 153);
  }

  input {
    border: 0px none;
    background: rgba(0, 0, 0, 0) none repeat scroll 0% 0%;
    color: rgb(0, 0, 0);
    font-size: 16px;
    -moz-box-flex: 1;
    flex-grow: 1;
    margin-left: 8px;
  }
</style>

<div class="search">
  <div class="input">
    <div class="icon">
      <SearchIcon />
    </div>

    <input aria-label="Search" placeholder="Search" />
  </div>
</div>
