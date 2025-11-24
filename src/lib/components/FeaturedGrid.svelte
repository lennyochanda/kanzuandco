<script lang="ts">
  export let title = 'Featured products';
  export let items = Array.from({ length: 4 }).map((_, i) => ({
    id: i,
    name: `Product ${i + 1}`,
    price: '$' + (29 + i * 10),
    img: `https://via.placeholder.com/280x200?text=Product+${i+1}`
  }));
</script>

<section class="featured">
  <div class="container">
    <div class="featured-header">
      <h2>{title}</h2>
      <a class="view-all" href="/">View all</a>
    </div>

    <div class="grid">
      {#each items as p}
        <article class="card">
          <div class="thumb">
            <img src={p.img} alt={p.name} />
          </div>
          <div class="meta">
            <div class="name">{p.name}</div>
            <div class="price">{p.price}</div>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<style>
  .featured { padding: 36px 0; }
  .container { max-width: 1200px; margin: 0 auto; padding: 0 24px; }
  .featured-header { display:flex; justify-content:space-between; align-items:center; margin-bottom:16px; }
  .featured-header h2 { margin:0; font-size:20px; }
  .view-all { color:#17AF26; text-decoration:none; font-size:14px; }
  .grid { display:grid; grid-template-columns:repeat(4,1fr); gap:16px; }
  .card { background:#fff; border-radius:8px; overflow:hidden; border:1px solid #F1F1F1; }
  .thumb img { width:100%; height:160px; object-fit:cover; display:block; }
  .meta { padding:12px; display:flex; justify-content:space-between; align-items:center; }
  .name { color:#111; font-size:14px; }
  .price { color:#062A09; font-weight:600; }

  @media (max-width: 900px) {
    .grid { grid-template-columns:repeat(2,1fr); }
  }

  @media (max-width: 480px) {
    .grid { grid-template-columns:1fr; }
  }
</style>
