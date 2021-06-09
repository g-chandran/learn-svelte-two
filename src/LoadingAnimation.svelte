<script>
  export let loaderColor = "orangered";
</script>

<div class="dots-2" style="color: {loaderColor}" />

<style>
  .dots-2 {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: currentColor;
    box-shadow: 0 0 0 3px;
    position: relative;
    animation: d2-0 2s infinite linear;
  }

  .dots-2:before,
  .dots-2:after {
    content: "";
    position: absolute;
    border-radius: 50%;
    inset: 0;
    background: currentColor;
    transform: rotate(0deg) translate(18px);
    animation: d2 1s infinite;
  }
  .dots-2:after {
    animation-delay: -0.5s;
  }

  @keyframes d2-0 {
    100% {
      transform: rotate(1turn);
    }
  }

  @keyframes d2 {
    100% {
      transform: rotate(1turn) translate(20px);
    }
  }
</style>
