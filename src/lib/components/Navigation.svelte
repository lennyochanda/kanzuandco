<script lang="ts">
  let cartCount = 0;
  let searchQuery = '';
  let isMobileMenuOpen = false;

  const toggleMobileMenu = () => {
    isMobileMenuOpen = !isMobileMenuOpen;
  };

  const handleSearch = () => {
    console.log('Search:', searchQuery);
  };
</script>

<nav class="navigation">
  <!-- Desktop Navigation -->
  <div class="nav-desktop">
    <!-- Main Navbar -->
    <div class="main-navbar">
      <div class="logo-section">
        <img
          src="https://cdn.builder.io/api/v1/image/assets/TEMP/1be5fd1f24f1302e1d869d8911e54e9785380d64?width=334"
          alt="Top Shelf British Columbia"
          class="logo-desktop"
        />
      </div>

      <div class="search-section">
        <div class="search-input-container">
          <input
            type="text"
            placeholder="Search"
            class="search-input"
            bind:value={searchQuery}
          />
        </div>
        <button class="search-button" on:click={handleSearch}>
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
            <path d="M8.625 15.75C12.56 15.75 15.75 12.56 15.75 8.625C15.75 4.68997 12.56 1.5 8.625 1.5C4.68997 1.5 1.5 4.68997 1.5 8.625C1.5 12.56 4.68997 15.75 8.625 15.75Z" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M16.5 16.5L15 15" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
      </div>

      <div class="account-section">
        <span class="account-text">Your Account</span>
        <div class="divider"></div>
        <div class="cart-container">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path d="M7.5 7.66952V6.69952C7.5 4.44952 9.31 2.23952 11.56 2.02952C14.24 1.76952 16.5 3.87952 16.5 6.50952V7.88952" stroke="#46494F" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M8.99983 22H14.9998C19.0198 22 19.7398 20.39 19.9498 18.43L20.6998 12.43C20.9698 9.99 20.2698 8 15.9998 8H7.99983C3.72983 8 3.02983 9.99 3.29983 12.43L4.04983 18.43C4.25983 20.39 4.97983 22 8.99983 22Z" stroke="#46494F" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M15.4955 12H15.5045" stroke="#46494F" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M8.49451 12H8.50349" stroke="#46494F" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <div class="cart-badge">{cartCount}</div>
        </div>
      </div>
    </div>

    <!-- Menu Navbar -->
    <div class="menu-navbar">
      <div class="menu-items">
        <a href="#" class="menu-item">Shop All</a>
        <div class="menu-item-dropdown">
          <span class="menu-item">Flower</span>
          <svg width="13" height="12" viewBox="0 0 13 12" fill="none">
            <path d="M10.46 4.47461L7.20004 7.73461C6.81504 8.11961 6.18504 8.11961 5.80004 7.73461L2.54004 4.47461" stroke="#46494F" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <a href="#" class="menu-item">Edibles</a>
        <div class="menu-item-dropdown">
          <span class="menu-item">Concentrates</span>
          <svg width="13" height="12" viewBox="0 0 13 12" fill="none">
            <path d="M10.46 4.47461L7.20004 7.73461C6.81504 8.11961 6.18504 8.11961 5.80004 7.73461L2.54004 4.47461" stroke="#46494F" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <a href="#" class="menu-item">Mushrooms</a>
        <div class="menu-item-dropdown">
          <span class="menu-item">Promotions/Bundles</span>
          <svg width="13" height="12" viewBox="0 0 13 12" fill="none">
            <path d="M10.46 4.47461L7.20004 7.73461C6.81504 8.11961 6.18504 8.11961 5.80004 7.73461L2.54004 4.47461" stroke="#46494F" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <div class="menu-item-dropdown">
          <span class="menu-item">Support</span>
          <svg width="13" height="12" viewBox="0 0 13 12" fill="none">
            <path d="M10.46 4.47461L7.20004 7.73461C6.81504 8.11961 6.18504 8.11961 5.80004 7.73461L2.54004 4.47461" stroke="#46494F" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <a href="#" class="menu-item">Rewards</a>
        <a href="#" class="menu-item">Blog</a>
      </div>
    </div>
  </div>

  <!-- Mobile Navigation -->
  <div class="nav-mobile">
    <!-- Mobile Header -->
    <div class="mobile-header">
      <div class="mobile-left">
        <button class="hamburger-menu" on:click={toggleMobileMenu}>
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path d="M3 7H21" stroke="#062A09" stroke-width="1.5" stroke-linecap="round"/>
            <path d="M3 12H21" stroke="#062A09" stroke-width="1.5" stroke-linecap="round"/>
            <path d="M3 17H21" stroke="#062A09" stroke-width="1.5" stroke-linecap="round"/>
          </svg>
        </button>
        <img
          src="https://cdn.builder.io/api/v1/image/assets/TEMP/a7034d720027906237e99411c439be7283ee46a1?width=238"
          alt="Top Shelf British Columbia"
          class="logo-mobile"
        />
      </div>

      <div class="mobile-right">
        <span class="account-text">Your Account</span>
        <div class="divider"></div>
        <div class="cart-container mobile-cart">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path d="M7.5 7.66952V6.69952C7.5 4.44952 9.31 2.23952 11.56 2.02952C14.24 1.76952 16.5 3.87952 16.5 6.50952V7.88952" stroke="#46494F" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M8.99983 22H14.9998C19.0198 22 19.7398 20.39 19.9498 18.43L20.6998 12.43C20.9698 9.99 20.2698 8 15.9998 8H7.99983C3.72983 8 3.02983 9.99 3.29983 12.43L4.04983 18.43C4.25983 20.39 4.97983 22 8.99983 22Z" stroke="#46494F" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M15.4955 12H15.5045" stroke="#46494F" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M8.49451 12H8.50349" stroke="#46494F" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <div class="cart-badge mobile-badge">{cartCount}</div>
        </div>
      </div>
    </div>

    <!-- Mobile Search -->
    <div class="mobile-search">
      <div class="mobile-search-input-container">
        <input
          type="text"
          placeholder="Search"
          class="mobile-search-input"
          bind:value={searchQuery}
        />
      </div>
      <button class="mobile-search-button" on:click={handleSearch}>
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <path d="M7.66634 13.9997C11.1641 13.9997 13.9997 11.1641 13.9997 7.66634C13.9997 4.16854 11.1641 1.33301 7.66634 1.33301C4.16854 1.33301 1.33301 4.16854 1.33301 7.66634C1.33301 11.1641 4.16854 13.9997 7.66634 13.9997Z" stroke="white" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M14.6663 14.6663L13.333 13.333" stroke="white" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
    </div>
  </div>
</nav>

<style>
  .navigation {
    background: #FFF;
    border-bottom: 1px solid #F4F4F4;
  }

  /* Desktop Navigation */
  .nav-desktop {
    display: none;
  }

  .main-navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 14px 64px;
    border-bottom: 1px solid #F4F4F4;
    height: 76px;
  }

  .logo-section {
    width: 270px;
  }

  .logo-desktop {
    width: 167px;
    height: 40px;
  }

  .search-section {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .search-input-container {
    display: flex;
    width: 400px;
    height: 48px;
    padding: 4px 4px 4px 24px;
    align-items: center;
    border-radius: 100px;
    border: 1px solid #F4F4F4;
    background: #FFF;
  }

  .search-input {
    flex: 1;
    border: none;
    outline: none;
    background: transparent;
    color: #46494F;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 150%;
  }

  .search-input::placeholder {
    color: #C8C9CB;
  }

  .search-button {
    display: flex;
    width: 48px;
    height: 48px;
    padding: 8px;
    justify-content: center;
    align-items: center;
    border-radius: 100px;
    background: #17AF26;
    border: none;
    cursor: pointer;
  }

  .account-section {
    display: flex;
    width: 270px;
    justify-content: flex-end;
    align-items: center;
    gap: 24px;
  }

  .account-text {
    color: #46494F;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 400;
    line-height: 150%;
  }

  .divider {
    width: 1px;
    height: 12px;
    background: #C8C9CB;
  }

  .cart-container {
    position: relative;
    display: flex;
    align-items: center;
  }

  .cart-badge {
    position: absolute;
    top: -6px;
    right: -6px;
    display: flex;
    width: 16px;
    height: 16px;
    justify-content: center;
    align-items: center;
    border-radius: 100px;
    background: #EB2606;
    color: #FFF;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 10px;
    font-weight: 400;
    line-height: 150%;
  }

  .menu-navbar {
    display: flex;
    padding: 16px 64px;
    justify-content: center;
    align-items: center;
    height: 56px;
  }

  .menu-items {
    display: flex;
    align-items: center;
    gap: 40px;
  }

  .menu-item {
    color: #46494F;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 150%;
    text-decoration: none;
  }

  .menu-item-dropdown {
    display: flex;
    align-items: center;
    gap: 6px;
    cursor: pointer;
  }

  .menu-item-dropdown svg {
    padding-top: 2px;
  }

  /* Mobile Navigation */
  .nav-mobile {
    display: block;
  }

  .mobile-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 14px 24px;
    border-bottom: 1px solid #F4F4F4;
    height: 56px;
  }

  .mobile-left {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .hamburger-menu {
    background: none;
    border: none;
    cursor: pointer;
    padding: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .logo-mobile {
    width: 119px;
    height: 28px;
  }

  .mobile-right {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    gap: 16px;
  }

  .mobile-cart {
    position: relative;
  }

  .mobile-badge {
    width: 14px;
    height: 14px;
    top: -4px;
    right: -4px;
    font-size: 8px;
  }

  .mobile-search {
    display: flex;
    padding: 12px 24px;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid #F4F4F4;
    height: 60px;
  }

  .mobile-search-input-container {
    display: flex;
    height: 36px;
    padding: 4px 20px;
    align-items: center;
    flex: 1;
    border-radius: 100px;
    border: 1px solid #F4F4F4;
    background: #FFF;
  }

  .mobile-search-input {
    flex: 1;
    border: none;
    outline: none;
    background: transparent;
    color: #46494F;
    font-family: Lexend, -apple-system, Roboto, Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 400;
    line-height: 150%;
  }

  .mobile-search-input::placeholder {
    color: #C8C9CB;
  }

  .mobile-search-button {
    display: flex;
    width: 36px;
    height: 36px;
    padding: 8px;
    justify-content: center;
    align-items: center;
    border-radius: 100px;
    background: #17AF26;
    border: none;
    cursor: pointer;
  }

  @media (min-width: 768px) {
    .nav-desktop {
      display: block;
    }

    .nav-mobile {
      display: none;
    }
  }
</style>
