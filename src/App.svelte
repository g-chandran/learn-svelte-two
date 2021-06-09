<script>
  import { onMount } from "svelte";
  import Response from "./Response.svelte";
  import LoadingAnimation from "./LoadingAnimation.svelte";

  let promise;
  const URL = "https://www.boredapi.com/api/activity";

  async function getActivity() {
    let request = await fetch(URL);
    let response = await request.json();

    if (request.ok) {
      console.log(response);
      return response;
    }
    throw new Error("Unable to fetch data");
  }

  onMount(() => {
    promise = getActivity();
  });

  function handleRequest() {
    promise = getActivity();
  }
</script>

<main>
  <button on:click={handleRequest}>Boredom on Boredom</button>
  <div class="container">
    {#await promise}
      <!-- <Stretch size="60" color="#FF3E00" unit="px" /> -->
      <LoadingAnimation />
      <p>...waiting</p>
    {:then results}
      {#if results}
        <Response result={results} />
      {/if}
    {:catch error}
      {error.message}
    {/await}
  </div>
</main>

<style>
  main {
    height: 98vh;
    margin: 0% auto;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    /* border: 2px solid orangered; */
    width: 60%;
    box-shadow: 0 0 10px orangered;
    border-radius: 8px;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
