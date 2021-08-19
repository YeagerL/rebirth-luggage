<template id="RebirthLuggageImages">
    <div class="rebirthLuggageImages">
        <div class="keyCodeInput">
            <div class="input-container">
                <input type="tel" v-model="keyCode1" @focus="$event.target.select()" @input="numberOnly($event)" numberOnlymaxlength="3" /><span class="label-text">-</span>
                <input type="tel" v-model="keyCode2" @focus="$event.target.select()" @input="numberOnly($event)" maxlength="2" /><span class="label-text">-</span>
                <input type="tel" v-model="keyCode3" @focus="$event.target.select()" @input="numberOnly($event)" maxlength="3" />
            </div>

            <div>
                <button @click="resetKeyCode()">Reset Code</button>
                <button @click="reset()">Reset All</button>
            </div>
        </div>

        <div>
            <div v-if="true" id="locationImages" class="locationImages">
                <div v-if="displayLocationImage1" id="locationImagePosition1">
                    <img class="locationImage" v-bind:class="{ selected: isSelectedImagePosition('1')}" :src="locationImage1" @click="selectPosition('1')" alt="" />
                    <h3>{{ locationImage1.toString().substring(48, locationImage1.length - 4) }}</h3>
                </div>
                <div v-if="displayLocationImage2" id="locationImagePosition2">
                    <img class="locationImage" v-bind:class="{ selected: isSelectedImagePosition('2') }" :src="locationImage2" @click="selectPosition('2')" alt="" />
                    <h3>{{ locationImage2.toString().substring(48, locationImage2.length - 4) }}</h3>
                </div>
                <div v-if="displayLocationImage3" id="locationImagePosition3">
                    <img class="locationImage" v-bind:class="{ selected: isSelectedImagePosition('3') }" :src="locationImage3" @click="selectPosition('3')" alt="" />
                    <h3>{{ locationImage3.toString().substring(48, locationImage3.length - 4) }}</h3>
                </div>
            </div>

            <div>
                <table class="rebirthImages">
                    <tbody>
                        <tr>
                            <td><img v-bind:class="{ selected : isSelected('1') }" @click="onClick('1')" src="./rebirthLuggageImages/Image-1.png" width="219" height="128" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('6') }" @click="onClick('6')" src="./rebirthLuggageImages/Image-6.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('11') }" @click="onClick('11')" src="./rebirthLuggageImages/Image-11.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('16') }" @click="onClick('16')" src="./rebirthLuggageImages/Image-16.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('22') }" @click="onClick('22')" src="./rebirthLuggageImages/Image-22.png" width="232" height="147" alt="" /></td>
                        </tr>
                        <tr>
                            <td><img v-bind:class="{ selected : isSelected('2') }" @click="onClick('2')" src="./rebirthLuggageImages/Image-2.png" width="224" height="135" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('7') }" @click="onClick('7')" src="./rebirthLuggageImages/Image-7.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('12') }" @click="onClick('12')" src="./rebirthLuggageImages/Image-12.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('17') }" @click="onClick('17')" src="./rebirthLuggageImages/Image-17.png" alt="" /></td>

                            <td><img v-bind:class="{ selected : isSelected('23') }" @click="onClick('23')" src="./rebirthLuggageImages/Image-23.png" alt="" /></td>
                        </tr>
                        <tr>
                            <td><img v-bind:class="{selected : isSelected('3') }" @click="onClick('3')" src="./rebirthLuggageImages/Image-3.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('8') }" @click="onClick('8')" src="./rebirthLuggageImages/Image-8.png" width="208" height="128" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('13') }" @click="onClick('13')" src="./rebirthLuggageImages/Image-13.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('18') }" @click="onClick('18')" src="./rebirthLuggageImages/Image-18.png" alt="" /></td>
                            
                            <td><img v-bind:class="{selected : isSelected('24') }" @click="onClick('24')" src="./rebirthLuggageImages/Image-24.png" alt="" /></td>
                        </tr>
                        <tr>
                            <td><img v-bind:class="{selected : isSelected('4') }" @click="onClick('4')" src="./rebirthLuggageImages/Image-4.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('9') }" @click="onClick('9')" src="./rebirthLuggageImages/Image-9.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('14') }" @click="onClick('14')" src="./rebirthLuggageImages/Image-14.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('19') }" @click="onClick('19')" src="./rebirthLuggageImages/Image-19.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('25') }" @click="onClick('25')" src="./rebirthLuggageImages/Image-25.png" width="248" height="162" alt="" /></td>
                        </tr>
                        <tr>
                            <td><img v-bind:class="{selected : isSelected('5') }" @click="onClick('5')" src="./rebirthLuggageImages/Image-5.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('10') }" @click="onClick('10')" src="./rebirthLuggageImages/Image-10.png" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('15') }" @click="onClick('15')" src="./rebirthLuggageImages/Image-15.png" width="229" height="145" alt="" /></td>
                            <td><img v-bind:class="{selected : isSelected('20') }" @click="onClick('20')" src="./rebirthLuggageImages/Image-20.png" alt="" /></td>
                            <td></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

    </div>

</template>

<script setup>
import { ref } from 'vue';
import './RebirthLuggageImages.css'
//import './RebirthLuggageImages.scss'

let keyCode1 = ref()
let keyCode2 = ref()
let keyCode3 = ref()

let locationImage1 = ref()
let locationImage2 = ref()
let locationImage3 = ref()

let displayLocationImage1 = ref('')
let displayLocationImage2 = ref('')
let displayLocationImage3 = ref('')

displayLocationImage1.value = false
displayLocationImage2.value = false
displayLocationImage3.value = false

//const locationImage1Open = locationImage1.value === undefined || locationImage1.value.length === 0
//const displayLocationImage1 = locationImage1.value !== undefined && locationImage1.value.length > 0

//const locationImage2Open = locationImage2.value === undefined || locationImage2.value.length === 0
//const displayLocationImage2 = locationImage2.value !== undefined && locationImage2.value.length > 0

let selectedPosition = null

let locationImage1Open = true
let locationImage2Open = true
let locationImage3Open = true

let selectedImages = []

    const onClick = (imageNumber) => {

        let currentlySelectedImages;
        if (selectedImages.filter(x => x.id === imageNumber).length > 0) {
            currentlySelectedImages = selectedImages.filter(x => { x.id !== imageNumber });
        } 
        else {
            currentlySelectedImages = selectedImages
        }

        // no position is selected and all three image positions are filled
        if (selectedPosition === null && !locationImage1Open && !locationImage2Open && !locationImage3Open) {
            return
            // selectedPosition = 3
        }

        //if (selectedPosition !== null || (selectedPosition === null && selectedImages.filter(x => x.id === imageNumber)).length === 0) {
            let locationImage = ''
            switch(imageNumber) {
                case "1": 
                    locationImage = "src/components/rebirthLuggageLocationImages/01 - Underneath Ramp At Security Comm Tower.jpg"
                    break
                case "2":
                    locationImage = "src/components/rebirthLuggageLocationImages/02 - Prison Reception - Underneath Staircase.jpg"
                    break
                case "3":
                    locationImage = "src/components/rebirthLuggageLocationImages/03 - 2nd Floor Decon - Above Circuit Breakers.jpg"
                    break
                case "4":
                    locationImage = "src/components/rebirthLuggageLocationImages/04 - Top Gondola.jpg"
                    break
                case "5":
                    locationImage = "src/components/rebirthLuggageLocationImages/05 - Shipping And Receiving - Behind Front Filing Cabinets.jpg"
                    break
                case "6":
                    locationImage = "src/components/rebirthLuggageLocationImages/06 - Bio - 3rd Floor - By Periodic Chart.jpg"
                    break
                case "7":
                    locationImage = "src/components/rebirthLuggageLocationImages/07 - 2nd Floor Cells - Lockers.jpg"
                    break
                case "8":
                    locationImage = "src/components/rebirthLuggageLocationImages/08 - 2nd Floor Chem - Under stairs.jpg"
                    break
                case "9":
                    locationImage = "src/components/rebirthLuggageLocationImages/09 - Shack Outside Construction - By Ladder.jpg"
                    break
                case "10":
                    locationImage = "src/components/rebirthLuggageLocationImages/10 - Harbor - Pipes Outside.jpg"
                    break
                case "11":
                    locationImage = "src/components/rebirthLuggageLocationImages/11 - Red Roof - Outside Behind Boxes.jpg"
                    break
                case "12":
                    locationImage = "src/components/rebirthLuggageLocationImages/12 - Comunication Office - Behind Ceiling Extention.jpg"
                    break
                case "13":
                    locationImage = "src/components/rebirthLuggageLocationImages/13 - Living Quarters - Top Room Bottom Bookshelf.jpg"
                    break
                case "14":
                    locationImage = "src/components/rebirthLuggageLocationImages/14 - 2nd Floor Chem - Under Desk Near Window.jpg"
                    break
                case "15":
                    locationImage = "src/components/rebirthLuggageLocationImages/15 - 2nd Building At Living Quarters Row - Bottom Windowless Room Above Bookshelf.jpg"
                    break
                case "16":
                    locationImage = "src/components/rebirthLuggageLocationImages/16 - Outside Construction Sheds - Under Zip - Behind Barrels.jpg"
                    break
                case "17":
                    locationImage = "src/components/rebirthLuggageLocationImages/17 - Nova Factory Watchtower - 3rd Floor - On Ceiling.jpg"
                    break
                case "18":
                    locationImage = "src/components/rebirthLuggageLocationImages/18 - Middle Of Chem Tunnel - Above Bodies.jpg"
                    break
                case "19":
                    locationImage = "src/components/rebirthLuggageLocationImages/19 - Inside Tunnel To Prison - Behind Power Unit.jpg"
                    break
                case "20":
                    locationImage = "src/components/rebirthLuggageLocationImages/20 - 2nd Floor Decon - Behing TV By Buy.jpg"
                    break
                case "21":
                    locationImage = "src/components/rebirthLuggageLocationImages/21 - Old Construction - Cement Mixer.jpg"
                    break
                case "22":
                    locationImage = "src/components/rebirthLuggageLocationImages/22 - Decon - Behind Crates Outside Stairs.jpg"
                    break
                case "23":
                    locationImage = "src/components/rebirthLuggageLocationImages/23 - Security Shack - Under Table.jpg"
                    break
                case "24":
                    locationImage = "src/components/rebirthLuggageLocationImages/24 - Living Quarter Row - Outside Parachute Above Air Conditioner.jpg"
                    break
                case "25":
                    locationImage = "src/components/rebirthLuggageLocationImages/25 - Nova - Middle Room - Behind Top Monitors.jpg"
                    break
                case "26":
                    locationImage = "src/components/rebirthLuggageLocationImages/26 - Bio - Basement Piping Cubby.jpg"
                    break
                default:
                    locationImage = ''
            }

            //if (selectedPosition === null && (locationImage1Open || locationImage2Open || locationImage3Open)) {
                selectedImages = [];
                selectedImages.push({ "id": imageNumber, "value": locationImage });

                if (currentlySelectedImages != undefined && currentlySelectedImages.length > 0) {
                    currentlySelectedImages.forEach(x => { selectedImages.push(x) });
                }
                
            //}

            if (selectedPosition === 1 || selectedPosition === null && locationImage1Open) {
                locationImage1.value = locationImage
                displayLocationImage1.value = true
                locationImage1Open = false
            } else if (selectedPosition === 2 || selectedPosition === null && locationImage2Open) {
                locationImage2.value = locationImage
                displayLocationImage2.value = true
                locationImage2Open = false
            } else if (selectedPosition === 3 || selectedPosition === null && locationImage3Open) {
                locationImage3.value = locationImage
                displayLocationImage3.value = true
                locationImage3Open = false
            }


        
            selectedPosition = null;
        //}
        
    };

    const selectPosition = (position) => {
        debugger
        selectedPosition = position
    }
    
    const isSelected = (imageNumber) => {
        if (selectedImages.length != 0) {
            return selectedImages.filter(x => x.id === imageNumber) != 0
        }
        return false
    }

    const isSelectedImagePosition = (imagePosition) => {
        if (selectedPosition != null) {
            return imagePosition === selectedPosition
        }
        return false
    }

    const reset = () => {
        selectedPosition = null
        locationImage1.value = ''
        locationImage2.value = ''
        locationImage3.value = ''

        locationImage1Open = true
        locationImage2Open = true
        locationImage3Open = true
        
        displayLocationImage1 = false
        displayLocationImage2 = false
        displayLocationImage3 = false

        selectedImages = []

        resetKeyCode()
    };

    const resetKeyCode = () => {
        keyCode1.value = ''
        keyCode2.value = ''
        keyCode3.value = ''
    }

    const numberOnly = (event) => {
        event.target.value = event.target.value.replace(/[^0-9]/gi, "")
    }

    const arrow = (event) => {
        debugger
        if (event.key === "ArrowRight") {
            
        }
    }

</script>