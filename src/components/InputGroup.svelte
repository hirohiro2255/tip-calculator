<script>
</script>

<section class="input-group">
  <div class="bill-group">
    <h3 class="tip-title">Bill</h3>
    <input class="bill-input" type="number" placeholder="0" />
    <small class="error-msg">Hello there</small>
  </div>
  <div class="tip-selection-group">
    <div class="tip-selection-header">
      <h3 class="tip-title">Select Tip %</h3>
      <button class="custom-button">Click to Custom</button>
    </div>
    <div class="tip-buttons-group">
      <div class="button-container">
        <button class="button">5%</button>
        <button class="delete-button"><i class="fa-solid fa-xmark" /></button>
      </div>
      <div class="button-container">
        <button class="button">10%</button>
        <button class="delete-button"><i class="fa-solid fa-xmark" /></button>
      </div>
      <div class="button-container">
        <button class="button">15%</button>
        <button class="delete-button"><i class="fa-solid fa-xmark" /></button>
      </div>
      <div class="button-container">
        <button class="button">20%</button>
        <button class="delete-button"><i class="fa-solid fa-xmark" /></button>
      </div>
    </div>
  </div>
  <div class="people-group">
    <h3 class="tip-title">Number of People</h3>
    <input class="number-of-people" type="number" placeholder="0" />
    <small class="error-msg">Hello there</small>
  </div>
</section>

<style>
  .tip-title {
    font-size: 1rem; /* same as size on desktop */
    font-weight: 700;
    color: var(--neutral-dark-grayish-cyan);
    line-height: 1.48125;
  }
  .bill-input {
    width: 100%;
    margin-top: 6px;
    height: 48px;
    border-style: none;
    border-radius: 5px;
    background-color: var(--neutral-very-light-grayish-cyan);
    font-size: 1.5rem; /* same as size on desktop */
    font-weight: 700;
    line-height: 1.48;
    text-align: right;
    background-image: url(./../assets/icon-dollar.svg);
    background-repeat: no-repeat;
    background-position: 17px center;
  }
  .bill-input:focus {
    outline: none;
    border: 2px solid var(--primary-strong-cyan);
  }
  .tip-selection-group {
    margin-top: 32px;
  }
  .tip-selection-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .custom-button {
    padding-top: 5px;
    padding-bottom: 5px;
    font-size: 0.9rem;
    font-weight: 700;
    line-height: 1.2;
    text-align: center;
    color: var(--neutral-white);
    border-radius: 5px;
    background-color: var(--neutral-dark-grayish-cyan);
    border-style: none;
  }
  .custom-button:hover {
    opacity: 0.7;
    transition: 0.3s;
  }
  .tip-buttons-group {
    margin-top: 16px;
    display: grid;
    grid-template: repeat(3, 48px) / 1fr 1fr;
    gap: 16px;
  }
  .button-container {
    display: flex;
  }
  .button {
    flex: 3;
    font-size: 1.5rem;
    font-weight: 700;
    line-height: 1.48;
    color: var(--neutral-white);
    background-color: var(--neutral-very-dark-cyan);
    border-radius: 5px;
    border-style: none;
  }
  .button:hover {
    background-color: hsla(173, 61%, 77%, 1);
    color: var(--neutral-very-dark-cyan);
    transition: 0.2s;
  }
  .delete-button {
    flex: 1;
    margin-left: 3px;
    font-size: 1.5rem;
    font-weight: 700;
    line-height: 1.48;
    color: var(--neutral-white);
    background-color: var(--neutral-error-red);
    border-radius: 5px;
    border-style: none;
  }
  .delete-button:hover {
    opacity: 0.7;
    transition: 0.2s;
  }
  .number-of-people {
    width: 100%;
    margin-top: 6px;
    height: 48px;
    border-style: none;
    border-radius: 5px;
    background-color: var(--neutral-very-light-grayish-cyan);
    font-size: 1.5rem; /* same as size on desktop */
    font-weight: 700;
    line-height: 1.48;
    text-align: right;
    background-image: url(./../assets/icon-person.svg);
    background-repeat: no-repeat;
    background-position: 17px center;
  }
  .number-of-people:focus {
    border: 2px solid var(--primary-strong-cyan);
    outline: none;
  }
  .error {
    border: 1px solid var(--neutral-error-red);
  }
  .error-msg {
    display: block;
    margin-top: 3px;
    font-size: 0.9rem;
    color: var(--neutral-error-red);
  }

  @media screen and (min-width: 768px) {
    .input-group {
      margin-top: 13px;
      width: 45%;
    }
    .tip-buttons-group {
      margin-top: 16px;
      display: grid;
      grid-template: repeat(2, 48px) / 1fr 1fr 1fr;
      gap: 14px;
    }
    .button-container {
      height: 38px;
    }
    .button {
      flex: 5;
    }
    .delete-button {
      flex: 1;
      margin-left: 2px;
    }
    .people-group {
      margin-top: 40px;
    }
  }
</style>
