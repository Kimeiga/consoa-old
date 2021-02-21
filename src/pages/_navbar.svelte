<script>
  import { onMount } from "svelte";
  export let profileImgURL;

  import halfmoon from "halfmoon";
</script>

<!-- <nav class="navbar">
	<a href="/"><h1>Consoa</h1></a>
	<a href="/feed">🧑‍🍼</a>
	<a href="/mail">📧</a>
	<a href="/user"><img src={profileImgURL} alt="profile" /></a>
</nav> -->

<nav class="navbar">
  <!-- Navbar content (with toggle sidebar button) -->
  <div class="navbar-content">
    <button
      class="btn btn-action"
      type="button"
      on:click={() => halfmoon.toggleSidebar()}
    >
      <!-- <i class="fa fa-bars" aria-hidden="true"></i> -->
      ☰
      <span class="sr-only">Toggle sidebar</span>
      <!-- sr-only = show only on screen readers -->
    </button>
  </div>
  <!-- Navbar brand -->
  <a href="/" class="navbar-brand"> Consoa </a>
  <!-- Navbar text -->
  <span class="navbar-text text-monospace badge font-size-12 px-5 px-sm-10"
    >v3.0</span
  >
  <!-- text-monospace = font-family shifted to monospace -->
  <!-- Navbar nav -->
  <ul class="navbar-nav d-none d-md-flex ml-auto">
    <!-- d-none = display: none, d-md-flex = display: flex on medium screens and up (width > 768px) -->
    <li class="nav-item active">
      <a href="#" class="nav-link">Docs</a>
    </li>
    <li class="nav-item">
      <a href="#" class="nav-link">Products</a>
    </li>
    <li class="nav-item">
      <a href="/user" class="nav-link">
        <img src={profileImgURL} alt="profile" style="height: 70%;" />
      </a>
    </li>
  </ul>

  <!-- Navbar content (with the dropdown menu) -->
  <div class="navbar-content d-md-none ml-auto">
    <!-- d-md-none = display: none on medium screens and up (width > 768px), ml-auto = margin-left: auto -->
    <div class="dropdown with-arrow">
      <button
        class="btn"
        data-toggle="dropdown"
        type="button"
        id="navbar-dropdown-toggle-btn-1"
      >
        Menu
        <i class="fa fa-angle-down" aria-hidden="true" />
      </button>
      <div
        class="dropdown-menu dropdown-menu-right w-200"
        aria-labelledby="navbar-dropdown-toggle-btn-1"
      >
        <!-- w-200 = width: 20rem (200px) -->
        <a href="#" class="dropdown-item">Docs</a>
        <a href="#" class="dropdown-item">Products</a>
        <div class="dropdown-divider" />
        <div class="dropdown-content">
          <form action="..." method="...">
            <div class="form-group">
              <input
                type="text"
                class="form-control"
                placeholder="Email address"
                required="required"
              />
            </div>
            <button class="btn btn-primary btn-block" type="submit"
              >Sign up</button
            >
          </form>
        </div>
      </div>
    </div>
  </div>
</nav>
