<script lang="ts">
  import { onMount } from 'svelte';

  export let mobile: boolean = false;

  type NavItem = {
    title: string;
    href?: string;
    panel?: {
      description?: string;
      columns?: Array<{ heading?: string; links: Array<{ title: string; href?: string }> }>
    }
  };

  // Expect `items` to be passed in from a parent (layout or page).
  export let items: NavItem[] = [];

  let activeIndex: number | null = null;
  let hideTimeout: number | null = null;

  function showPanel(i: number) {
    if (hideTimeout) {
      clearTimeout(hideTimeout);
      hideTimeout = null;
    }
    activeIndex = i;
  }

  function hidePanelDelayed() {
    // small delay so users can move pointer into panel
    hideTimeout = window.setTimeout(() => {
      activeIndex = null;
      hideTimeout = null;
    }, 150);
  }

  function hidePanelNow() {
    if (hideTimeout) {
      clearTimeout(hideTimeout);
      hideTimeout = null;
    }
    activeIndex = null;
  }

  function handleKeydown(e: KeyboardEvent) {
    if (e.key === 'Escape') hidePanelNow();
  }

  onMount(() => {
    window.addEventListener('keydown', handleKeydown);
    return () => window.removeEventListener('keydown', handleKeydown);
  });
</script>

{#if !mobile}
  <div class="menu-items" role="menubar">
    {#each items as item, i}
      <div
        class="menu-item-wrapper"
        role="presentation"
        on:mouseenter={() => item.panel && showPanel(i)}
        on:mouseleave={() => item.panel && hidePanelDelayed()}
      >
        {#if item.panel}
          <button class="menu-item menu-button" class:open={activeIndex === i} on:focus={() => showPanel(i)} on:blur={() => hidePanelDelayed()} aria-haspopup="true" aria-expanded={activeIndex === i}>
            {item.title}
            <svg width="13" height="12" viewBox="0 0 13 12" fill="none">
              <path d="M10.46 4.47461L7.20004 7.73461C6.81504 8.11961 6.18504 8.11961 5.80004 7.73461L2.54004 4.47461" stroke="#46494F" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        {:else}
          <a class="menu-item" href={item.href || '/'}>{item.title}</a>
        {/if}

        {#if item.panel}
          <div
            class="panel {activeIndex === i ? 'visible' : ''}"
            on:mouseenter={() => showPanel(i)}
            on:mouseleave={() => hidePanelDelayed()}
            role="group"
            aria-hidden={activeIndex === i ? 'false' : 'true'}
          >
            {#if item.panel.description}
              <div class="panel-description">{item.panel.description}</div>
            {/if}

            {#if item.panel.columns}
              <div class="panel-grid">
                {#each item.panel.columns as col}
                  <div class="panel-col">
                    {#if col.heading}
                      <div class="col-heading">{col.heading}</div>
                    {/if}
                    <ul>
                      {#each col.links as link}
                        <li><a href={link.href || '/'} class="col-link">{link.title}</a></li>
                      {/each}
                    </ul>
                  </div>
                {/each}
              </div>
            {/if}
          </div>
        {/if}
      </div>
    {/each}
  </div>
{:else}
  <nav class="mobile-menu-items">
    {#each items as item}
      <a href={item.href || '/'} class="mobile-menu-item">{item.title}</a>
    {/each}
  </nav>
{/if}

<style>
  .menu-items {
    display: flex;
    align-items: center;
    gap: 40px;
  }

  .menu-item-wrapper {
    position: relative;
  }

  /* menu-skeleton removed (layout provides items) */

  .menu-button {
    background: none;
    border: none;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 4px 6px;
  }

  .menu-button svg {
    transition: transform 180ms ease;
    transform-origin: center;
  }

  .menu-button.open svg {
    transform: rotate(180deg);
  }

  .menu-item {
    color: #46494F;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 150%;
    text-decoration: none;
  }

  /* dropdown helpers removed (styles moved into component) */

  .mobile-menu-items {
    display: flex;
    flex-direction: column;
    gap: 12px;
    padding-top: 8px;
  }

  .mobile-menu-item {
    color: #46494F;
    text-decoration: none;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 16px;
    font-weight: 500;
    padding: 8px 0;
  }

  /* Panel styles */
  .panel {
    position: absolute;
    top: calc(100% + 8px);
    left: 50%;
    transform: translateX(-50%) translateY(6px);
    min-width: 360px;
    max-width: 840px;
    background: linear-gradient(180deg, #ffffff 0%, #fbfdff 100%);
    border-radius: 12px;
    border: 1px solid rgba(15, 23, 42, 0.06);
    box-shadow: 0 14px 40px rgba(8, 24, 48, 0.12);
    padding: 20px;
    z-index: 60;
    visibility: hidden;
    opacity: 0;
    transition: opacity 160ms ease, transform 200ms cubic-bezier(.2,.9,.2,1), visibility 160ms;
  }

  .panel.visible {
    visibility: visible;
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }

  .panel::before {
    content: '';
    position: absolute;
    top: -8px;
    left: 50%;
    transform: translateX(-50%);
    width: 12px;
    height: 12px;
    background: #FFF;
    border-left: 1px solid rgba(15, 23, 42, 0.06);
    border-top: 1px solid rgba(15, 23, 42, 0.06);
    transform-origin: center;
    transform: translateX(-50%) rotate(45deg);
    box-shadow: -6px -6px 12px rgba(8, 24, 48, 0.04);
  }

  .panel-description {
    font-size: 14px;
    color: #6b6f76;
    margin-bottom: 12px;
  }

  .panel-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px 28px;
  }

  .panel-col {
    min-width: 140px;
  }

  .col-heading {
    font-weight: 600;
    margin-bottom: 8px;
    color: #111;
  }

  .col-link {
    color: #46494F;
    text-decoration: none;
    display: block;
    padding: 4px 0;
    transition: color 120ms ease, transform 120ms ease;
  }

  .col-link:hover {
    color: #062A09;
    transform: translateX(4px);
  }

  .menu-item, .menu-button {
    color: #2b2f33;
    transition: color 120ms ease, background 120ms ease;
  }

  .menu-item:hover, .menu-button:hover {
    color: #062A09;
  }

  @media (max-width: 1024px) {
    .panel { max-width: 640px; grid-template-columns: repeat(2,1fr); }
    .panel-grid { grid-template-columns: repeat(2,1fr); }
  }
</style>
