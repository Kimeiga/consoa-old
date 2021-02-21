<script>
  import { Router } from "@roxi/routify";
  import { routes } from "../.routify/routes";
  import { onMount } from "svelte";

  if (
    window.matchMedia &&
    window.matchMedia("(prefers-color-scheme: dark)").matches
  ) {
    document.body.classList.add("dark");
  }
  import { FirebaseApp } from "sveltefire";

  import firebase from "firebase/app";
  import "firebase/firestore";
  import "firebase/auth";
  import "firebase/performance";
  import "firebase/analytics";

  // For Firebase JS SDK v7.20.0 and later, measurementId is optional
  const firebaseConfig = {
    apiKey: "AIzaSyCFy5PZuwwjmJRJEJvZklCgYJw9iyEJrzM",
    authDomain: "consoa.firebaseapp.com",
    projectId: "consoa",
    storageBucket: "consoa.appspot.com",
    messagingSenderId: "893906171047",
    appId: "1:893906171047:web:25e9cc1ab1643c8cea5782",
    measurementId: "G-H5233MBHTG",
  };

  if (!firebase.apps.length) {
    firebase.initializeApp(firebaseConfig);
  } else {
    firebase.app(); // if already initialized, use that one
  }

  import halfmoon from "halfmoon";
  onMount(() => {
    halfmoon.onDOMContentLoaded();
  });
</script>

<!-- Modals go here -->
<!-- Reference: https://www.gethalfmoon.com/docs/modal -->

<div
  id="page-wrapper"
  class="page-wrapper with-navbar with-sidebar with-navbar-fixed-bottom with-transitions"
  data-sidebar-type="overlayed-all"
  data-sidebar-hidden="hidden"
  data-dm-shortcut-enabled="true"
  data-sidebar-shortcut-enabled="true"
>
  <FirebaseApp {firebase}>
    <Router {routes} />
  </FirebaseApp>
</div>

<style global>
  @import "../assets/global.css";
</style>
