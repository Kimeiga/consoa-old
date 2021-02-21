<script>
  import { Router } from "@roxi/routify";
  import { routes } from "../.routify/routes";

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

  require("halfmoon/css/halfmoon-variables.min.css");
  import halfmoon from "halfmoon";
</script>

<FirebaseApp {firebase}>
  <Router {routes} />
</FirebaseApp>
