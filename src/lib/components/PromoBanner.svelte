<script lang="ts">
  export let text = 'Free shipping on orders over $50 — limited time only.';
</script>

<div class="promo-banner">
  <div class="container">{text}</div>
</div>

<style>
  .promo-banner {
    background: linear-gradient(90deg,#E6FFEC,#F1FFF5);
    color: #062A09;
    padding: 10px 0;
    border-bottom: 1px solid rgba(6,42,9,0.06);
    font-family: Lexend, system-ui, -apple-system, Roboto, Helvetica, Arial, sans-serif;
    font-size: 13px;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 24px;
    text-align: center;
  }
</style>
