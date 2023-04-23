<script>
  import InputGroup from './components/InputGroup.svelte';
  import OutputGroup from './components/OutputGroup.svelte';
  import logo from './assets/logo.svg';

  let bill = 0;
  let people = 0;
  let selectedTip = 0;
  let tipOptions = [5, 10, 15, 20];

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
      console.log('Empty!');
      return;
    }
    const parsedBill = Number.parseFloat(event.detail.bill);
    if (parsedBill <= -1) {
      console.log('negative number!!');
    } else if (isNaN(parsedBill)) {
      console.log('NaN!!');
    } else if (parsedBill.toString().length >= 6) {
      console.log('too high');
      return;
    } else {
      // implementation for the parsable input
      bill = parsedBill;
      console.log(bill);
    }
  }

  function handlePeople(event) {
    if (event.detail.people.length === 0) {
      return;
    }
    const parsedNumber = Number.parseInt(event.detail.people, 10);
    if (parsedNumber <= -1) {
    } else if (isNaN(parsedNumber)) {
    } else if (parsedNumber.toString().length >= 19) {
      console.log('Really? a lot!!');
    } else {
      people = parsedNumber;
      console.log(people);
    }
  }

  function handleTip(event) {
    const { tip } = event.detail;
    selectedTip = tip;
  }

  function handleDeleteOption(event) {
    const { tipOption } = event.detail;
    tipOptions = tipOptions.filter((option) => {
      return option !== tipOption;
    });
    selectedTip = selectedTip === tipOption ? 0 : selectedTip;
  }

  function resetButton() {
    bill = 0;
    people = 0;
    selectedTip = null;
  }
</script>

<img src={logo} alt="logo" />

<section class="form-container">
  <div class="form-wrapper">
    <InputGroup
      {bill}
      {people}
      {tipOptions}
      {selectedTip}
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
