<template>
  <div>
    <div class="keypad">
      <!--<input v-model='code' class="keyCode" type='text' placeholder='________' /> -->

      <div class="keyCodeContainer">
        <div class="keyCode">
          {{ code }}
        </div>
      </div>
    
      <table class="keyboard" cellSpacing="10px">
        <tbody align="center" class="keyboard-body">
          <tr>
            <td><button class="key numberKey" @click="onKeyPress('1')">1</button></td>
            <td><button class="key numberKey">2</button></td>
            <td><button class="key numberKey">3</button></td>
            <td rowspan="3"><button class="key submitKey" >Submit</button></td>
          </tr>
          <tr>
            <td><button class="key numberKey">4</button></td>
            <td><button class="key numberKey">5</button></td>
            <td><button class="key numberKey">6</button></td>
          </tr>
          <tr>
            <td><button class="key numberKey">7</button></td>
            <td><button class="key numberKey">8</button></td>
            <td><button class="key numberKey">9</button></td>
          </tr>
          <tr>
            <td><button class="key numberKey">&lt;</button></td>
            <td><button class="key numberKey">0</button></td>
            <td><button class="key numberKey">-</button></td>
            <td><button class="key resetKey">Reset</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import './keypad.css'
import {defineProps, reactive } from 'vue'

    const onKeyPress = (value) => {
        if (code === undefined || code.value === null) {
            code = ''
        }

        code += value
    }

</script>
