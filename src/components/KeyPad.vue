<template id="KeyPad">
  <div>
    <div class="keypad">
      <div class="keyCodeContainer">
        <div class="key-code">
          <input type="text" v-bind:class="{ selected: isSelected('keyCode1') }" v-model="keyCode1" @focus="setFocus($event, 'keyCode1')" @input="numberOnly($event)" maxlength="3" data-disable-touch-keyboard />
          <span class="label-text">-</span>
          <input type="text" v-bind:class="{ selected: isSelected('keyCode2') }" v-model="keyCode2" @focus="setFocus($event, 'keyCode2')" @input="numberOnly($event)" maxlength="2" id="keyCode2" data-disable-touch-keyboard />
          <span class="label-text">-</span>
          <input type="text" v-bind:class="{ selected: isSelected('keyCode3') }" v-model="keyCode3" @focus="setFocus($event, 'keyCode3')" @input="numberOnly($event)" maxlength="3" data-disable-touch-keyboard />
        </div>
      </div>
    
      <table class="keyboard" cellSpacing="10px">
        <tbody align="center" class="keyboard-body">
          <tr>
            <td><button class="key numberKey" @click="onKeyPress('1')">1</button></td>
            <td><button class="key numberKey" @click="onKeyPress('2')">2</button></td>
            <td><button class="key numberKey" @click="onKeyPress('3')">3</button></td>
            <td><button class="key back-key" @click="onBackspace()">back</button></td>
          </tr>
          <tr>
            <td><button class="key numberKey" @click="onKeyPress('4')">4</button></td>
            <td><button class="key numberKey" @click="onKeyPress('5')">5</button></td>
            <td><button class="key numberKey" @click="onKeyPress('6')">6</button></td>
            <td rowspan="2"><button class="key resetKey" @click="resetKeyCode()">Reset Code</button></td>
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

<script>
import './keypad.css'

export default {
  data() {
    return {
      selectedInput: 'keyCode1',
      keyCode1: '',
      keyCode2: '',
      keyCode3: ''
    }
  },
  mounted: function () {
    this.selectedInput = 'keyCode1'
  },
  methods: {
    isSelected(input) {
      return this.selectedInput === input
    },
    createNewValue(input, newInputValue) {
      // let currentInputValue = this.getInputValue(input)
      let currentInputValue = this[this.selectedInput]

      let maxLength = 0
      if (input === 'keyCode1' || input === 'keyCode3') {
        maxLength = 3
      }
      else if (input === 'keyCode2') {
        maxLength = 2
      }

      let newValue = ''
      if (currentInputValue.length === maxLength) {
        let partialCurrentValue = currentInputValue.slice(1).toString()
        newValue = partialCurrentValue += newInputValue
        return newValue
      }

      newValue = currentInputValue += newInputValue
      return newValue
    },
    appendValue(input, value) {
      let newValue = this.createNewValue(input, value);
      this[this.selectedInput] = newValue
      // this.setValue(input, newValue)
    },
    /* getInputValue(input) {
      if (input === 'keyCode1') {
        return this.keyCode1
      }

      if (input === 'keyCode2') {
        return this.keyCode2
      }

      if (input === 'keyCode3') {
        return this.keyCode3
      }
    }, */ 
    /* setValue(input, value) {
      if (input === 'keyCode1') {
        this.keyCode1 = value
        return
      }

      if (input === 'keyCode2') {
        this.keyCode2 = value
        return
      }

      if (input === 'keyCode3') {
        this.keyCode3 = value
        return
      }
    }, */
    onBackspace() {
      if (this.selectedInput === 'keyCode1' && this.keyCode1.length === 0) {
        return;
      }

      const inputValue = this[this.selectedInput]
      // const inputValue = this.getInputValue(this.selectedInput);

      if (inputValue.length === 0) {
        return
      }

      const value = inputValue.substr(0, inputValue.length - 1);
      this[this.selectedInput] = value
      // this.setValue(this.selectedInput, value)
    },
    setFocus(event, input) {
      this.selectedInput = input
      event.target.blur()
    },
    onKeyPress(value) {
      this.appendValue(this.selectedInput, value)
    },
    numberOnly(event) {
      event.target.value = event.target.value.replace(/[^0-9]/gi, "")
    },
    resetKeyCode() {
      this.keyCode1 = ''
      this.keyCode2 = ''
      this.keyCode3 = ''

      this.selectedInput = 'keyCode1'
    }
  }
}

</script>
