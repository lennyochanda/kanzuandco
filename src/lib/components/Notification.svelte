<script lang="ts">
  import { onMount, onDestroy } from 'svelte';

  let hours = 23;
  let minutes = 15;
  let seconds = 0;
  let interval: NodeJS.Timeout;

  const updateCountdown = () => {
    if (seconds > 0) {
      seconds--;
    } else if (minutes > 0) {
      minutes--;
      seconds = 59;
    } else if (hours > 0) {
      hours--;
      minutes = 59;
      seconds = 59;
    }
  };

  onMount(() => {
    interval = setInterval(updateCountdown, 1000);
  });

  onDestroy(() => {
    if (interval) {
      clearInterval(interval);
    }
  });

  $: formattedTime = `${hours.toString().padStart(2, '0')} : ${minutes.toString().padStart(2, '0')} : ${seconds.toString().padStart(2, '0')}`;
</script>

<div class="notification-bar">
  <div class="offer-text">LIMITED OFFER: 30% OFF. Use RABBIT30 at Checkout.</div>
  <div class="countdown-timer">{formattedTime}</div>
</div>

<style>
  .notification-bar {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 16px;
    background: #05422C;
    padding: 8px 24px;
    width: 100%;
    min-height: 37px;
  }

  .offer-text {
    color: rgba(255, 255, 255, 0.7);
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 12px;
    font-weight: 400;
    line-height: 150%;
    flex: 1;
    text-align: center;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .countdown-timer {
    color: #FFF;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 12px;
    font-weight: 400;
    line-height: 150%;
    white-space: nowrap;
  }

  @media (min-width: 768px) {
    .notification-bar {
      padding: 8px 0px;
    }

    .offer-text {
      font-size: 14px;
      flex: none;
    }

    .countdown-timer {
      font-size: 14px;
    }
  }
</style>
