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
  import { FirebaseApp, User, Doc, Collection } from "sveltefire";

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

  // Include CSS file
  /*
  Or,
  Include the following (no variables, supports IE11):
  require("halfmoon/css/halfmoon.min.css");
*/

  // // Import JS library
  // import halfmoon from "halfmoon";

  // onMount(() => {
  //   halfmoon.onDOMContentLoaded();
  // });
</script>

<FirebaseApp {firebase}>
  <Router {routes} />
</FirebaseApp>

<style global>
  @import "halfmoon/css/halfmoon-variables.min.css";
  /* @import "../assets/global.css";
  @import "chota/dist/chota.css";

  body.dark {
    --bg-color: #000;
    --bg-secondary-color: #131316;
    --font-color: #f5f5f5;
    --color-grey: #ccc;
    --color-darkGrey: rgb(56, 56, 56);
  }

  .nav a,
  .nav .brand {
    color: var(--color-lightGrey);
  } */
</style>
