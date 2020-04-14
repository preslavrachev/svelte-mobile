<script>
  import Image from "../common/Image.svelte";

  export let imageSrc;
  export let header;
  export let title;
  export let subtitle;
</script>

<style>
  .card {
    position: relative;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    border: 1px solid transparent;
    text-align: left;
  }

  .content {
    display: flex;
    flex-direction: column;
    background-color: rgb(255, 255, 255);
    padding: 12px;
    color: rgb(0, 0, 0);
    -moz-box-flex: 1;
    flex-grow: 1;
  }

  .header {
    font-weight: 600;
    font-size: 13px;
    line-height: 120%;
    text-transform: lowercase;
    font-variant: all-small-caps;
    color: rgb(33, 150, 243);
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .title {
    font-weight: 500;
    font-size: 17px;
    line-height: 120%;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .title:not(:last-child) {
    margin-bottom: 4px;
  }

  .subtitle {
    font-size: 13px;
    line-height: 140%;
    display: -webkit-box;
    -moz-box-orient: vertical;
    -webkit-line-clamp: 3;
    overflow: hidden;
    color: rgb(108, 108, 108);
  }

  .float {
    filter: drop-shadow(rgba(0, 0, 0, 0.15) 0px 4px 6px);
  }

  .rounded {
    border-radius: 8px;
  }

  .image-container {
    position: relative;
    width: 100%;
    padding-bottom: 100%;
  }

  .spacer {
    -moz-box-flex: 1;
    flex-grow: 1;
  }

  .footer {
    display: flex;
    -moz-box-align: center;
    align-items: center;
    -moz-box-pack: justify;
    justify-content: space-between;
  }

  .footer .left {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  .footer .right {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }

  .footer .left .item,
  .footer .right .item {
    display: flex;
    -moz-box-align: center;
    align-items: center;
    font-weight: 600;
    font-size: 13px;
    line-height: 140%;
    height: 32px;
  }
</style>

<div class="card float rounded">
  {#if imageSrc}
    <div class="image-container">
      <Image src={imageSrc} />
    </div>
  {/if}
  <div class="content">
    <div class="header">{header}</div>
    <div class="title">{title}</div>
    <div class="subtitle">{subtitle}</div>
    <div class="spacer">
      <div class="footer">
        <div class="left">
          <div class="item">Left</div>
        </div>
        <div class="right">
          <div class="item">Right</div>
        </div>
      </div>
    </div>
  </div>
</div>
