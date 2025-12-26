<script>
  export const ssr = false;
  import favicon from "$lib/assets/favicon.svg";
  import { goto } from "$app/navigation";
  import { onMount } from "svelte";
  import "../app.css";

  let { children } = $props();

  function navigate() {
    const token = localStorage.getItem("token");
    if (token) {
      goto("/dashboard/contacts");
    } else {
      goto("/login");
    }
  }

  onMount(() => {
    navigate();
  });
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

{@render children()}
