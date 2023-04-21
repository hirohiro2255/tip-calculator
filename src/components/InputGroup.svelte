<script>
</script>

<section class="input-group">
  <div class="bill-group">
    <h3 class="tip-title">Bill</h3>
    <input class="bill-input" type="number" placeholder="0" />
    <small>Hello there</small>
  </div>
  <div class="tip-selection-group">
    <div class="tip-selection-header">
      <h3 class="tip-title">Select Tip %</h3>
      <button class="custom-button">Add Button</button>
    </div>
    <div class="tip-buttons-group">
      <button class="button">5%</button>
      <button class="button">10%</button>
      <button class="button">15%</button>
    </div>
  </div>
  <div class="people-group">
    <h3 class="tip-title">Number of People</h3>
    <input class="number-of-people" type="number" placeholder="0" />
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
  .tip-selection-group {
    margin-top: 32px;
  }
  .tip-selection-header {
    display: flex;
    justify-content: space-between;
  }
  .custom-button {
    font-size: 1.2rem;
    font-weight: 700;
    line-height: 1.2;
    text-align: right;
    color: var(--neutral-white);
    border-radius: 5px;
    background-color: var(--neutral-dark-grayish-cyan);
    border-style: none;
  }
  .tip-buttons-group {
    margin-top: 16px;
    display: grid;
    grid-template: repeat(3, 48px) / 1fr 1fr;
    gap: 16px;
  }
  .button {
    font-size: 1.5rem;
    font-weight: 700;
    line-height: 1.48;
    color: var(--neutral-white);
    background-color: var(--neutral-very-dark-cyan);
    border-radius: 5px;
    border-style: none;
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
</style>
