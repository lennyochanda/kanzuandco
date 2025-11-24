<script lang="ts">
  // simple footer scaffold to extend later
  export let year = new Date().getFullYear();
</script>

<footer class="site-footer">
  <div class="container">
    <div class="cols">
      <div class="col">
        <h4>Customer Service</h4>
        <ul>
          <li><a href="/">Help Center</a></li>
          <li><a href="/">Shipping</a></li>
          <li><a href="/">Returns</a></li>
        </ul>
      </div>
      <div class="col">
        <h4>Company</h4>
        <ul>
          <li><a href="/">About</a></li>
          <li><a href="/">Careers</a></li>
          <li><a href="/">Press</a></li>
        </ul>
      </div>
      <div class="col">
        <h4>Legal</h4>
        <ul>
          <li><a href="/">Terms</a></li>
          <li><a href="/">Privacy</a></li>
        </ul>
      </div>
      <div class="col newsletter">
        <h4>Subscribe</h4>
        <p>Get deals and updates</p>
        <form on:submit|preventDefault={() => {}}>
          <input type="email" placeholder="Email address" />
          <button type="submit">Subscribe</button>
        </form>
      </div>
    </div>

    <div class="bottom">
      <div>© {year} Your Shop</div>
      <div class="social">Follow us — <a href="/">Instagram</a> · <a href="/">Facebook</a></div>
    </div>
  </div>
</footer>

<style>
  .site-footer { background:#FAFAFA; border-top:1px solid #EFEFEF; padding:32px 0; font-family:Lexend,system-ui,Roboto,Helvetica,Arial; }
  .container { max-width:1200px; margin:0 auto; padding:0 24px; }
  .cols { display:grid; grid-template-columns:repeat(4,1fr); gap:20px; margin-bottom:20px; }
  .col h4 { margin:0 0 8px 0; font-size:14px; }
  .col ul { list-style:none; padding:0; margin:0; }
  .col li { margin:6px 0; }
  .col a { color:#333; text-decoration:none; font-size:14px; }
  .newsletter input { padding:8px; width:100%; margin-bottom:8px; border:1px solid #E6E6E6; border-radius:6px; }
  .newsletter button { background:#17AF26; color:#fff; border:none; padding:8px 12px; border-radius:6px; cursor:pointer; }
  .bottom { display:flex; justify-content:space-between; color:#6b6f76; font-size:13px; }

  @media (max-width:900px) { .cols { grid-template-columns:repeat(2,1fr); } }
  @media (max-width:600px) { .cols { grid-template-columns:1fr; } .bottom{flex-direction:column; gap:8px;} }
</style>
