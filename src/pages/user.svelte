<script>
  import RoutifyIntro from "./example/_components/RoutifyIntro.svelte";
  import { metatags } from "@roxi/routify";
  metatags.title = "My Routify app";
  metatags.description = "Description coming soon...";
  import { getContext } from "svelte";
  import { FirebaseApp, User, Doc, Collection } from "sveltefire";

  import { goto } from "@roxi/routify";

  let user;

  $: if (!user) {
    // $goto("/");
  }
</script>

<main class="container">
  <!-- 1. 🔥 Firebase App -->
  <!-- 2. 😀 Get the current user -->
  <User let:user let:auth on:user={(e) => (user = e.detail.user)}>
    <h1>Hi {user.displayName}</h1>

    <img src={user.photoURL} alt="profile" />

    <h2>Name</h2>
    <p>{user.displayName}</p>
    <h2>Email</h2>
    <p>{user.email}</p>

    <button
      on:click={() => {
        auth.signOut();
        $goto("/");
      }}>Sign Out</button
    >
  </User>
</main>
