<script>
  export let result;
  let accessibility = result.accessibility * 100;
  $: price = result.price * 100;
</script>

<div class="container">
  <span class="title">{result.activity}</span>

  <p>Accessibility</p>
  <div class="meter">
    <div class="measure" style="width: {accessibility}%;">{accessibility}%</div>
  </div>
  <p>Price</p>
  <div class="meter">
    <div class="measure" style="width: {price}%;">{price}%</div>
  </div>
  <h3>{result.participants}</h3>
  <h3>{result.type}</h3>
  <h3>{result.link}</h3>
</div>

<style>
  * {
    margin: 0;
  }

  .title {
    font-size: x-large;
    color: orangered;
    font-weight: normal;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  h3 {
    font-weight: normal;
    font-size: medium;
  }

  .meter {
    width: 300px;
    height: 30px;
    background-color: rgba(100, 99, 99, 0.76);
    border-radius: 30px;
  }

  .measure {
    height: 100%;
    border-radius: 30px;
    background-color: orangered;
    text-align: center;
    align-items: center;
    color: white;
    font-size: small;
  }
</style>
