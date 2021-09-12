<template id="KeyPad">
  <div>
    <div class="keypad">
      <!--<input v-model='code' class="keyCode" type='text' placeholder='________' /> -->

      <div class="keyCodeContainer">
        <div class="keyCode">
          <input type="text" v-model="keyCode1" @focus="setFocus($event, 'keyCode1')" @input="numberOnly($event)" maxlength="3" /><span class="label-text">-</span>
          <input type="text" v-model="keyCode2" @focus="setFocus($event, 'keyCode2')" @input="numberOnly($event)" maxlength="2" id="keyCode2" /><span class="label-text">-</span>
          <input type="text" v-model="keyCode3" @focus="setFocus($event, 'keyCode3')" @input="numberOnly($event)" maxlength="3" />
        </div>
      </div>
    
      <table class="keyboard" cellSpacing="10px">
        <tbody align="center" class="keyboard-body">
          <tr>
            <td><button class="key numberKey" @click="onKeyPress('1')">1</button></td>
            <td><button class="key numberKey" @click="onKeyPress('2')">2</button></td>
            <td><button class="key numberKey" @click="onKeyPress('3')">3</button></td>
            <td><button class="key back-key" @click="onBackspace()">&lt;</button></td>
          </tr>
          <tr>
            <td><button class="key numberKey" @click="onKeyPress('4')">4</button></td>
            <td><button class="key numberKey" @click="onKeyPress('5')">5</button></td>
            <td><button class="key numberKey" @click="onKeyPress('6')">6</button></td>
            <td rowspan="2"><button class="key resetKey" @click="resetKeyCode()">Reset</button></td>
          </tr>
          <tr>
            <td><button class="key numberKey" @click="onKeyPress('7')">7</button></td>
            <td><button class="key numberKey" @click="onKeyPress('8')">8</button></td>
            <td><button class="key numberKey" @click="onKeyPress('9')">9</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import './keypad.css'
import { defineProps, reactive } from 'vue'

  let selectedInput = 'keyCode1'

  let keyCode1 = ref()
  let keyCode2 = ref()
  let keyCode3 = ref()

  keyCode1.value = '';
  keyCode2.value = '';
  keyCode3.value = '';

  const setNewValue = (input, newInputValue) => {
    let currentInputValue = getInputValue(input);

    let maxLength = 0;
    if (input === 'keyCode1' || input === 'keyCode3') {
      maxLength = 3;
    }
    else if (input === 'keyCode2') {
      maxLength = 2;
    }

    if (currentInputValue.length === maxLength) {
      return newInputValue;
    }

    let newValue = currentInputValue += newInputValue;
    return newValue;
  }

  const appendValue = (input, value) => {
    let newValue = setNewValue(input, value);

    if (input === 'keyCode1') {
      keyCode1.value = newValue;

      if (keyCode1.value.toString().length === 3) {
        selectedInput = 'keyCode2'
      }
      return
    }

    if (input === 'keyCode2') {
      keyCode2.value = newValue;

      if (keyCode2.value.toString().length === 2) {
        selectedInput = 'keyCode3'
      }
      return
    }

    if (input === 'keyCode3') {
      /* if (keyCode3.value.toString().length === 3) {
        let leftSide = keyCode3.value.substr(0, 2);
        keyCode3.value = leftSide += value;
        return
      } */

      keyCode3.value = newValue;
      return
    }
  }

  const selectPreviousInput = () => {
    if (selectedInput === 'keyCode2') {
      selectedInput = 'keyCode1'
      return
    }

    if (selectedInput === 'keyCode3') {
      selectedInput = 'keyCode2'
      return
    }
  }

  const getInputValue = (input) => {
    if (input === 'keyCode1') {
      return keyCode1.value
    }

    if (input === 'keyCode2') {
      return keyCode2.value
    }

    if (input === 'keyCode3') {
      return keyCode3.value
    }
  }

  const setValue = (input, value) => {
    if (input === 'keyCode1') {
      keyCode1.value = value
    }

    if (input === 'keyCode2') {
      keyCode2.value = value
    }

    if (input === 'keyCode3') {
      keyCode3.value = value
    }
  }

  const onBackspace = () => {
    if (selectedInput === 'keyCode1' && keyCode1.value.length === 0) {
      return
    }

    let inputValue = getInputValue(selectedInput);
    let value = '';
    if (inputValue.length > 0) {
      value = inputValue.substr(0, inputValue.length - 1);
      setValue(selectedInput, value)
      if (value.length === 0) {
        selectPreviousInput();
      }
    }

  }

  const setFocus = (event, input) => {
    selectedInput = input
    event.target.select()
  }

  const onKeyPress = (value) => {
    appendValue(selectedInput, value)
  }

  const numberOnly = (event) => {
    event.target.value = event.target.value.replace(/[^0-9]/gi, "")
  }

  const resetKeyCode = () => {
    keyCode1.value = ''
    keyCode2.value = ''
    keyCode3.value = ''

    selectedInput = 'keyCode1'
  }

</script>
