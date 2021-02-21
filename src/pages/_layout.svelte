<!-- routify:options preload="proximity" -->
<script>
  import { User } from "sveltefire";
</script>

<!-- Page wrapper with .with-navbar class -->
<User let:user let:auth>
  <div class="page-wrapper with-navbar">
    <!-- Navbar (immediate child of the page wrapper) -->
    <nav class="navbar">
      <!-- Navbar content (with toggle sidebar button) -->
      <div class="navbar-content">
        <button class="btn btn-action" type="button">
          <i class="fa fa-bars" aria-hidden="true" />
          <span class="sr-only">Toggle sidebar</span>
          <!-- sr-only = show only on screen readers -->
        </button>
      </div>
      <!-- Navbar brand -->
      <a href="/" class="navbar-brand">
        <!-- <img src="..." alt="..." /> -->
        Consoa
      </a>
      <!-- Navbar text -->
      <span class="navbar-text text-monospace">v1.0</span>
      <!-- text-monospace = font-family shifted to monospace -->
      <!-- Navbar nav -->
      <ul class="navbar-nav d-none d-md-flex">
        <!-- d-none = display: none, d-md-flex = display: flex on medium screens and up (width > 768px) -->
        <li class="nav-item active">
          <a href="/" class="nav-link">Feed</a>
        </li>
        <li class="nav-item">
          <a href="/messages" class="nav-link">Messages</a>
        </li>
        <li class="nav-item">
          <a href="/user" class="nav-link">User</a>
        </li>
      </ul>
      <!-- Navbar form (inline form) -->
      <form
        class="form-inline d-none d-md-flex ml-auto"
        action="..."
        method="..."
      >
        <!-- d-none = display: none, d-md-flex = display: flex on medium screens and up (width > 768px), ml-auto = margin-left: auto -->
        <input
          type="text"
          class="form-control"
          placeholder="Email address"
          required="required"
        />
        <button class="btn btn-primary" type="submit">Sign up</button>
      </form>
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

    <!-- Content wrapper -->
    <div class="content-wrapper">
      <slot />
    </div>
  </div>
</User>
