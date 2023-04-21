<script>
  import InputGroup from './components/InputGroup.svelte';
  import OutputGroup from './components/OutputGroup.svelte';
  import logo from './assets/logo.svg';
</script>

<img src={logo} alt="logo" />

<section class="form-container">
  <div class="form-wrapper">
    <InputGroup />
    <OutputGroup />
  </div>
</section>

<style>
  .form-container {
    box-shadow: 0px 32px 43px 0px hsla(185, 38%, 50%, 0.2);
    border-radius: 25px 25px 0px 0px;
    background-color: var(--neutral-white);
    width: 100%;
    max-width: 920px;
    padding-top: 32px;
    padding-right: 32px;
    padding-left: 32px;
    padding-bottom: 32px;
    margin-top: clamp(2.5625rem, 1.5282rem + 4.4131vw, 5.5rem);
  }

  .form-wrapper {
    display: flex;
    flex-direction: column;
  }
</style>
