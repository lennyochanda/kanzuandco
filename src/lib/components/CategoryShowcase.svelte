<script lang="ts">
  export let categories = [
    { title: 'Home & Kitchen', img: 'https://via.placeholder.com/520x280?text=Home' },
    { title: 'Clothing', img: 'https://via.placeholder.com/520x280?text=Clothing' },
    { title: 'Electronics', img: 'https://via.placeholder.com/520x280?text=Electronics' }
  ];
</script>

<section class="categories">
  <div class="container">
    <div class="grid">
      {#each categories as cat}
        <a class="tile" href="/">
          <img src={cat.img} alt={cat.title} />
          <div class="tile-label">{cat.title}</div>
        </a>
      {/each}
    </div>
  </div>
</section>

<style>
  .categories { padding: 28px 0; }
  .container { max-width:1200px; margin:0 auto; padding:0 24px; }
  .grid { display:grid; grid-template-columns:repeat(3,1fr); gap:16px; }
  .tile { display:block; position:relative; border-radius:10px; overflow:hidden; text-decoration:none; color:inherit; }
  .tile img { width:100%; height:200px; object-fit:cover; display:block; filter:contrast(1.02); }
  .tile-label { position:absolute; left:16px; bottom:12px; background:rgba(0,0,0,0.5); color:#fff; padding:8px 12px; border-radius:6px; font-weight:600; }

  @media (max-width:900px) { .grid { grid-template-columns:repeat(2,1fr); } }
  @media (max-width:480px) { .grid { grid-template-columns:1fr; } }
</style>
