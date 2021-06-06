<script>
  import { onMount } from "svelte";
  import { Stretch } from "svelte-loading-spinners";
  import Response from "./Response.svelte";

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
  <div>
    {#await promise}
      <Stretch size="60" color="#FF3E00" unit="px" />
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

<!-- <style>
  * {
    margin: 0;
  }
  p {
    text-align: center;
    font-size: 3rem;
    color: white;
    padding: 20px 60px;
  }

  main {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  div {
    border: 2px solid green;
    border-radius: 8px;
    background-color: green;
  }

  div:hover {
    box-shadow: 0px 0px 10px green;
  }
</style> -->
