<script>
  import RoutifyIntro from "./example/_components/RoutifyIntro.svelte";
  import { metatags } from "@roxi/routify";
  metatags.title = "My Routify app";
  metatags.description = "Description coming soon...";

  import { FirebaseApp, User, Doc, Collection } from "sveltefire";
  import { getContext } from "svelte";
  import Navbar from "_navbar.svelte";
  const firebase = getContext("firebase").getFirebase();

  const googleProvider = new firebase.auth.GoogleAuthProvider();

  let postText = "";
</script>

<main>
  <!-- 1. 🔥 Firebase App -->
  <!-- 2. 😀 Get the current user -->
  <User let:user let:auth>
    <!-- <nav class="nav">
      <div class="nav-left">
        <a class="active">🧑‍🍼</a>
      </div>
      <div class="nav-center">
        <a class="brand"> Consoa </a>
      </div>
      <div class="nav-right">
        <a>✉</a>
        <a href="/user"><img src={user.photoURL} alt="profile" /></a>
      </div>
    </nav> -->

    <!-- <Navbar profileImgURL={user.photoURL} /> -->

    <div slot="signed-out">
      <div
        class="hero is-full-screen"
        style="display: flex;
    flex-direction: column;"
      >
        <div
          class="is-center is-vertical-align"
          style="flex: 1;
    flex-direction: column;"
        >
          <h1>Consoa</h1>
          <h3>haki's social network ;)</h3>
          <hr />
          <button on:click={() => auth.signInWithPopup(googleProvider)}>
            Sign In With Google
          </button>
        </div>
        <nav class="tabs is-center">
          <a href="#features">features</a>
          <a href="#start">start</a>
          <a href="#docs">docs</a>
          <a href="https://github.com/jenil/chota">GitHub</a>
        </nav>
      </div>
    </div>

    <hr />

    <Collection
      path={"posts"}
      query={(ref) => ref.orderBy("createdAt")}
      let:data={posts}
      let:ref={postsRef}
      log
    >
      {#if !posts.length}
        No posts yet...
      {/if}

      {#each posts as post}
        <p>
          {JSON.stringify(post, Object.keys(post).sort())}
        </p>
        <button on:click={() => post.ref.delete()}>Delete</button>
      {/each}

      <input type="text" bind:value={postText} />

      <button
        on:click={() =>
          postsRef.add({
            text: postText,
            createdAt: Date.now(),
          })}
      >
        Add Post
      </button>

      <span slot="loading">Loading posts...</span>
    </Collection>

    <!-- 3. 📜 Get a Firestore document owned by a user -->
    <Doc path={`posts/${user.uid}`} let:data={post} let:ref={postRef} log>
      <h2>{post.title}</h2>

      <p>
        Document created at <em>{new Date(post.createdAt).toLocaleString()}</em>
      </p>

      <span slot="loading">Loading post...</span>
      <span slot="fallback">
        <button
          on:click={() =>
            postRef.set({
              title: "📜 I like Svelte",
              createdAt: Date.now(),
            })}
        >
          Create Document
        </button>
      </span>

      <!-- 4. 💬 Get all the comments in its subcollection -->

      <h3>Comments</h3>
      <Collection
        path={postRef.collection("comments")}
        query={(ref) => ref.orderBy("createdAt")}
        let:data={comments}
        let:ref={commentsRef}
        log
      >
        {#if !comments.length}
          No comments yet...
        {/if}

        {#each comments as comment}
          <p />
          <p>
            {comment.text}
            <button on:click={() => comment.ref.delete()}>Delete</button>
          </p>
        {/each}

        <button
          on:click={() =>
            commentsRef.add({
              text: "💬 Me too!",
              createdAt: Date.now(),
            })}
        >
          Add Comment
        </button>

        <span slot="loading">Loading comments...</span>
      </Collection>
    </Doc>
  </User>
</main>
