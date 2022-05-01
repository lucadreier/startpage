<script>
  import Icon from "@iconify/svelte";
  import { theme } from "./store.js";

  export let bookmarks;
</script>

#boilerplate

<div class={$theme === "dark" ? "wrap theme-dark" : "wrap theme-light"}>
  <button
    class="change-theme"
    on:click={() => theme.set($theme === "dark" ? "light" : "dark")}
  >
    {#if $theme === "dark"}
      <Icon icon="fa-regular:sun" />
    {:else if $theme === "light"}
      <Icon icon="fa-regular:moon" />
    {/if}
  </button>

  <div class="grid">
    {#each bookmarks as bookmark}
      <a class="grid__item" href={bookmark.url}>
        <Icon icon={bookmark.icon} class="icon" />
        {bookmark.title}
      </a>
    {/each}
  </div>
</div>

<style>
  .wrap {
    display: flex;
    justify-content: center;
    align-content: center;
    height: 100%;
  }

  .change-theme {
    border: none;
    outline: none;
    background: none;
    line-height: 0;
    font-size: 20px;

    position: absolute;
    top: 20px;
    right: 20px;
  }

  .theme-dark .change-theme {
    color: #b5b4c9;
  }

  .theme-light .change-theme {
    color: #242424;
  }

  .wrap.theme-dark {
    background: #151515;
  }

  .wrap.theme-light {
    background: #fdfdfd;
  }

  .theme-dark .grid__item {
    background: #1c1c1c;
    color: #b5b4c9;
  }

  .theme-dark .grid__item:hover {
    background: #242424;
    box-shadow: 0 0 50px rgba(256, 256, 256, 0.07);
  }

  .theme-light .grid__item {
    background: #b5b4c9;
    color: #1c1c1c;
  }

  .theme-light .grid__item:hover {
    background: #1c1c1c;
    color: #b5b4c9;
    box-shadow: 0 0 50px rgba(0, 0, 0, 0.17);
  }

  .grid {
    width: 75%;
    margin: auto;
    font-size: 26px;
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-column-gap: 20px;
    grid-row-gap: 20px;
  }

  .grid__item {
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 160px;

    display: flex;
    justify-content: center;
    align-items: center;
  }

  :global(.icon) {
    margin-right: 5px;
  }

  @media screen and (max-width: 1024px) {
    .grid {
      width: 100%;
      grid-template-columns: repeat(3, 1fr);
      padding: 10px 30px;
      font-size: 20px;
    }
    .grid__item {
      grid-area: auto !important;
    }
  }

  @media screen and (max-width: 768px) {
    .grid {
      width: 100%;
      grid-template-columns: repeat(2, 1fr);
      padding: 5px 15px;
    }
  }

  .grid__item:hover {
    cursor: pointer;
  }

  .grid__item:nth-child(1) {
    grid-area: 1 / 1 / 3 / 2;
  }
  .grid__item:nth-child(2) {
    grid-area: 1 / 2 / 2 / 3;
  }
  .grid__item:nth-child(3) {
    grid-area: 1 / 3 / 2 / 4;
  }
  .grid__item:nth-child(4) {
    grid-area: 1 / 4 / 3 / 5;
  }
  .grid__item:nth-child(5) {
    grid-area: 1 / 5 / 2 / 7;
  }
  .grid__item:nth-child(6) {
    grid-area: 2 / 2 / 3 / 3;
  }
  .grid__item:nth-child(7) {
    grid-area: 2 / 3 / 3 / 4;
  }
  .grid__item:nth-child(8) {
    grid-area: 2 / 5 / 3 / 7;
  }
  .grid__item:nth-child(9) {
    grid-area: 3 / 1 / 4 / 2;
  }
  .grid__item:nth-child(10) {
    grid-area: 3 / 2 / 4 / 3;
  }
  .grid__item:nth-child(11) {
    grid-area: 3 / 3 / 4 / 4;
  }
  .grid__item:nth-child(12) {
    grid-area: 3 / 4 / 4 / 5;
  }
</style>
