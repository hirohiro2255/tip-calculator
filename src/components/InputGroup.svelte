<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  const ENTER = 'Enter';
  const ESCAPE = 'Escape';

  export let bill = 0;
  export let people = 0;
  export let tipOptions = [];
  export let selectedTip;
  export let editing;
  export let billErrorMsg = '';
  export let peopleErrorMsg = '';

  $: addTipButtonEnabled = tipOptions.length >= 5;

  function handleInput(event) {
    dispatch('handleBill', {
      bill: event.target.value,
    });
  }
  function handlePeople(event) {
    dispatch('handlePeople', {
      people: event.target.value,
    });
  }
  function handleTip(tip) {
    dispatch('handleTip', {
      tip,
    });
  }
  function handleDeleteOption(val) {
    dispatch('handleDeleteOption', {
      tipOption: val,
    });
  }
  function handleCustom() {
    dispatch('handleCustom');
  }
  function removeFocus(event) {
    dispatch('removeFocus');
  }
  function finishEditing(event) {
    if (event.key === ENTER || event.key === ESCAPE) {
      dispatch('finishEditing');
    }
  }

  function handleNewTip(event) {
    dispatch('handleNewTip', {
      newTip: event.target.value
    });
  }
</script>

<section class="input-group">
  <div class="bill-group">
    <h3 class="tip-title">Bill</h3>
    <input
      class={ billErrorMsg.length === 0 ?  "bill-input" : "error-input"}
      type="text"
      placeholder="0"
      on:input={handleInput}
      bind:value={bill}
    />
    <small class="error-msg">{billErrorMsg}</small>
  </div>
  <div class="tip-selection-group">
    <div class="tip-selection-header">
      <h3 class="tip-title">Select Tip %</h3>
    </div>
    <div class="tip-buttons-group">
      {#if editing}
        <div class="button-container">
          <input class="add-input-text" autofocus
          type="number"
          on:input={handleNewTip}
          on:blur={removeFocus}
          on:keydown={finishEditing} />
        </div>
      {:else}
        <div class="button-container">
          <button disabled={addTipButtonEnabled} on:click={handleCustom} class="custom-button">Custom</button>
        </div>
      {/if}
      {#each tipOptions as obj (obj.id)}
        <div class="button-container">
          <button
            class={selectedTip === obj.tip ? 'focusedButton' : 'button'}
            on:click={() => handleTip(obj.tip)}>{obj.tip}%</button
          >
          <button class="delete-button" on:click={() => handleDeleteOption(obj.tip)}
            ><i class="fa-solid fa-xmark" /></button
          >
        </div>
      {/each}
    </div>
  </div>
  <div class="people-group">
    <h3 class="tip-title">Number of People</h3>
    <input
      on:input={handlePeople}
      bind:value={people}
      class={ peopleErrorMsg.length === 0 ?  "number-of-people" : "error-input"}
      type="text"
      placeholder="0"
    />
    <small class="error-msg">{peopleErrorMsg}</small>
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
  /*.custom-button {
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
  }*/
  .custom-button:hover {
    opacity: 0.7;
    transition: 0.3s;
  }
  .custom-button:disabled,
  .custom-button[disabled] {
    opacity: 0.2;
  }
  .add-input-text {
    width: 100%;
    text-align: right;
    font-size: 1.5rem; /* same as size on desktop */
    font-weight: 700;
    line-height: 1.48;
  }
  .tip-buttons-group {
    margin-top: 16px;
    display: grid;
    grid-template: repeat(3, 48px) / 1fr 1fr;
    gap: 16px;
  }
  .people-group {
    margin-top: 32px;
  }
  .button-container {
    display: flex;
  }
  .custom-button {
    flex: 5;
    font-size: 0.8rem;
    font-weight: 700;
    line-height: 1.48;
    color: var(--neutral-white);
    background-color: var(--neutral-dark-grayish-cyan);
    border-radius: 5px;
    border-style: none;
  }
  .button {
    flex: 5;
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
  .button:focus {
    background-color: hsla(173, 61%, 77%, 1);
    color: var(--neutral-very-dark-cyan);
  }
  .focusedButton {
    flex: 5;
    font-size: 1.5rem;
    font-weight: 700;
    line-height: 1.48;
    border-radius: 5px;
    border-style: none;
    background-color: hsla(173, 61%, 77%, 1);
    color: var(--neutral-very-dark-cyan);
  }
  .button:active {
    opacity: 0.5;
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
  .error-input {
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
    border: 2px solid var(--neutral-error-red);
  }
  .error-input:focus {
    outline: none;
    border: 2px solid var(--neutral-error-red); 
  }
  /*.error-input:active {
    outline: none;
    border: 2px solid var(--neutral-error-red); 
  }*/
  .error-msg {
    display: block;
    margin-top: 3px;
    font-size: 0.9rem;
    height: 22px;
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
    .error-input {
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
      border: 2px solid var(--neutral-error-red);
    }
    .error-input:focus {
      border: 2px solid var(--neutral-error-red); 
    }
  }
</style>
