<script>
  import InputGroup from './components/InputGroup.svelte';
  import OutputGroup from './components/OutputGroup.svelte';
  import logo from './assets/logo.svg';

  let bill = 0;
  let people = 1;
  let newTip = null;
  let selectedTip = 0;
  let tipOptions = [{ id: uuid(), tip: 5}, { id: uuid(), tip: 10}];
  let editing = false;
  let billErrorMsg = '';
  let peopleErrorMsg = '';

  function checkType(v) {
    return Object.prototype.toString.call(v);
  }

  // https://github.com/sveltejs/svelte-todomvc/blob/master/src/TodoMVC.svelte
  function uuid() {
    return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, (c) => {
      const r = Math.random() * 16 | 0;
      const v = c == 'x' ? r : (r & 0x3 | 0x8);
      return v.toString(16);
    });
  }

  function handleBill(event) {
    /**
     * input patterns
     *
     * 1. parsable input (into number) -> NOT ERROR
     * 2. empty (when initial page loading and all the input deleted) -> NOT ERROR
     * 3. unparsable input -> Error
     * 4. negative number -> Error
     * 4. too high price (19 digit length or higher in this case) -> Possibly Error
     * check if input is empty -> check if input is parsable
     */
    // const n = Number.parseInt(event.detail.bill, 10);
    if (event.detail.bill.length === 0) {
      bill = event.detail.bill;
      billErrorMsg = '';
      return;
    }
    const parsedBill = Number.parseFloat(event.detail.bill);
    if (parsedBill <= -1) {
      billErrorMsg = 'Cannot accept negative number'

    } else if (isNaN(parsedBill)) {
      billErrorMsg = 'Cannot accept non-numeric letters';
    } else if (parsedBill.toString().length >= 6) {
      billErrorMsg = 'Input must be less than 6-digits-length'
    } else {
      // implementation for the parsable input
      // bill = parsedBill;
      billErrorMsg = '';
    }
    bill = parsedBill;
  }

  function handlePeople(event) {
    if (event.detail.people.length === 0) {
      people = event.detail.people;
      peopleErrorMsg = '';
      return;
    }
    const parsedNumber = Number.parseInt(event.detail.people, 10);
    if (parsedNumber <= -1) {
      peopleErrorMsg = 'Cannot accept negative number'
    } else if (isNaN(parsedNumber)) {
      peopleErrorMsg = 'Cannot accept non-numeric letters';
    } else if (parsedNumber.toString().length >= 19) {
      peopleErrorMsg = 'Really? a lot!!'
    } else {
      peopleErrorMsg = ''
    }
    people = parsedNumber;
  }

  function handleTip(event) {
    const { tip } = event.detail;
    selectedTip = tip;
  }

  function handleDeleteOption(event) {
    const { tipOption } = event.detail;
    tipOptions = tipOptions.filter((option) => {
      return option.tip !== tipOption;
    });
    selectedTip = selectedTip === tipOption ? 0 : selectedTip;
  }

  function resetButton() {
    bill = 0;
    people = 0;
    selectedTip = null;
    billErrorMsg = '';
    peopleErrorMsg = '';
  }

  function handleCustom() {
    editing = true;
  }

  function removeFocus() {
    editing = false;
    if (checkType(newTip) === '[object Number]') {
      for (let i = 0; i < tipOptions.length; i++) {
        if (tipOptions[i].tip === newTip) {
          return;
        }
      }
      tipOptions = [...tipOptions, { id: uuid(), tip: newTip }]
    }
    newTip = null;
  }

  function finishEditing() {
    editing = false;
    if (checkType(newTip) === '[object Number]') {
      for (let i = 0; i < tipOptions.length; i++) {
        if (tipOptions[i].tip === newTip) {
          return;
        }
      }
      tipOptions = [...tipOptions, { id: uuid(), tip: newTip }]
    }
    newTip = null;
  }

  function handleNewTip(event) {
    const n = Number.parseInt(event.detail.newTip, 10);
    if (isNaN(n) || n >= 100 || n <= -1) {
      return;
    }
    newTip = n;

  }

</script>

<img src={logo} alt="logo" />

<section class="form-container">
  <div class="form-wrapper">
    <InputGroup
      {editing}
      {bill}
      {people}
      {tipOptions}
      {selectedTip}
      {billErrorMsg}
      {peopleErrorMsg}
      on:handleNewTip={handleNewTip}
      on:finishEditing={finishEditing}
      on:removeFocus={removeFocus}
      on:handleCustom={handleCustom}
      on:handleTip={handleTip}
      on:handleBill={handleBill}
      on:handlePeople={handlePeople}
      on:handleDeleteOption={handleDeleteOption}
    />
    <OutputGroup on:resetButton={resetButton} {bill} {people} {selectedTip} />
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
  @media screen and (min-width: 768px) {
    .form-container {
      border-radius: 25px;
    }
    .form-wrapper {
      flex-direction: row;
      justify-content: space-between;
      /* align-items: center; */
    }
  }
</style>
