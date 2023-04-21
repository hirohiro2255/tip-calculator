<section class="output-group">
  <div class="output-wrapper">
    <div class="tip-amount-group">
      <div class="tip-amount-header-group">
        <h3 class="tip-amount-header">Tip Amount</h3>
        <p class="person">/ person</p>
      </div>
      <h4 class="tip-amount">$4.27</h4>
    </div>

    <div class="total-amount-group">
      <div class="total-amount-header-group">
        <h3 class="total-amount-header">Total</h3>
        <p class="person">/ person</p>
      </div>
      <h4 class="total-amount">$32.79</h4>
    </div>

    <button class="reset-button">RESET</button>
  </div>
</section>

<style>
  .output-group {
    background-color: var(--neutral-very-dark-cyan);
    margin-top: 32px;
    padding-top: 37px;
    padding-right: clamp(1.4375rem, 1.0634rem + 1.5962vw, 2.5rem);
    padding-left: clamp(1.4375rem, 1.0634rem + 1.5962vw, 2.5rem);
    padding-bottom: clamp(1.5rem, 1.1479rem + 1.5023vw, 2.5rem);
    border-radius: 15px;
  }
  .tip-amount-group {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .tip-amount-header {
    color: var(--neutral-white);
    font-size: 1rem;
    font-weight: 700;
    line-height: 1.48125;
  }
  .total-amount-group {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .total-amount-header {
    color: var(--neutral-white);
    font-size: 1rem;
    font-weight: 700;
    line-height: 1.48125;
  }
  .person {
    color: var(--neutral-grayish-cyan);
    font-size: 0.8125rem;
    font-weight: 700;
    line-height: 1.48;
  }
  .tip-amount {
    color: var(--primary-strong-cyan);
    font-size: clamp(2rem, 1.6479rem + 1.5023vw, 3rem);
    line-height: 1.48;
    letter-spacing: -0.67px;
  }
  .total-amount {
    color: var(--primary-strong-cyan);
    font-size: clamp(2rem, 1.6479rem + 1.5023vw, 3rem);
    line-height: 1.48;
    letter-spacing: -0.67px;
  }
  .reset-button {
    padding-top: 9px;
    padding-bottom: 9px;
    margin-top: clamp(2rem, 0.0194rem + 8.4507vw, 7.625rem);
    width: 100%;
    background-color: var(--primary-strong-cyan);
    color: var(--neutral-very-dark-cyan);
    font-size: 1.25rem;
    font-weight: 700;
    line-height: 1.481;
    border-style: none;
    border-radius: 5px;
  }
</style>
