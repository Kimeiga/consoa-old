<!-- routify:options preload="proximity" -->
<script>
  import { FirebaseApp, User, Doc, Collection } from "sveltefire";
  import Navbar from "./_navbar.svelte";
  import halfmoon from "halfmoon";
</script>

<!-- Page wrapper start -->
<User let:user let:auth>
  <Navbar profileImgURL={user.photoURL} />

  <!-- Sidebar overlay -->
  <div class="sidebar-overlay" on:click={() => halfmoon.toggleSidebar()} />
  <!-- Sidebar start -->
  <div class="sidebar">
    <div class="sidebar-menu">
      <div class="sidebar-content">
        <input type="text" class="form-control" placeholder="Search" />
        <div class="mt-10 font-size-12">
          Press <kbd>/</kbd> to focus
        </div>
      </div>
      <h5 class="sidebar-title">Getting started</h5>
      <div class="sidebar-divider" />
      <a href="#" class="sidebar-link sidebar-link-with-icon active">
        <span class="sidebar-icon">
          <i class="fa fa-code" aria-hidden="true" />
        </span>
        Installation
      </a>
      <a href="#" class="sidebar-link sidebar-link-with-icon">
        <span class="sidebar-icon">
          <i class="fa fa-terminal" aria-hidden="true" />
        </span>
        CLI commands
      </a>
      <br />
      <h5 class="sidebar-title">Components</h5>
      <div class="sidebar-divider" />
      <a href="#" class="sidebar-link sidebar-link-with-icon">
        <span class="sidebar-icon">
          <i class="fa fa-folder-open-o" aria-hidden="true" />
        </span>
        File explorer
      </a>
      <a href="#" class="sidebar-link sidebar-link-with-icon">
        <span class="sidebar-icon">
          <i class="fa fa-table" aria-hidden="true" />
        </span>
        Spreadsheet
      </a>
      <a href="#" class="sidebar-link sidebar-link-with-icon">
        <span class="sidebar-icon">
          <i class="fa fa-map-o" aria-hidden="true" />
        </span>
        Map
      </a>
      <a href="#" class="sidebar-link sidebar-link-with-icon">
        <span class="sidebar-icon">
          <i class="fa fa-commenting-o" aria-hidden="true" />
        </span>
        Messenger
      </a>
    </div>
  </div>
  <!-- Sidebar end -->

  <!-- Content wrapper start -->
  <div class="content-wrapper">
    <div class="container-fluid">
      <slot />
    </div>
  </div>
  <!-- Content wrapper end -->
</User>
<!-- Page wrapper end -->
