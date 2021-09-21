<template id="RebirthLuggageImages">
    <div class="rebirth-luggage-images">
        <div>
            <vue-easy-lightbox
            scrollDisabled
            escDisabled
            moveDisabled
            :visible="visible"
            :imgs="imgs"
            :index="index"
            @hide="handleHide"
            ></vue-easy-lightbox>
        </div>

        <div id="images">
            <div v-if="!displayKeypad">
                <table class="rebirth-images">
                    <tbody>
                        <tr>
                            <td><img v-bind:class="{ selected : isSelected('1') }" @click="onClick('1')" src="./rebirthLuggageImages/Image-1.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('5') }" @click="onClick('5')" src="./rebirthLuggageImages/Image-5.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('9') }" @click="onClick('9')" src="./rebirthLuggageImages/Image-9.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('13') }" @click="onClick('13')" src="./rebirthLuggageImages/Image-13.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('17') }" @click="onClick('17')" src="./rebirthLuggageImages/Image-17.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('22') }" @click="onClick('22')" src="./rebirthLuggageImages/Image-22.png" alt="" /></td>
                        </tr>
                        <tr>
                            <td><img v-bind:class="{ selected : isSelected('2') }" @click="onClick('2')" src="./rebirthLuggageImages/Image-2.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('6') }" @click="onClick('6')" src="./rebirthLuggageImages/Image-6.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('10') }" @click="onClick('10')" src="./rebirthLuggageImages/Image-10.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('14') }" @click="onClick('14')" src="./rebirthLuggageImages/Image-14.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('18') }" @click="onClick('18')" src="./rebirthLuggageImages/Image-18.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('23') }" @click="onClick('23')" src="./rebirthLuggageImages/Image-23.png" alt="" /></td>
                        </tr>
                        <tr>
                            <td><img v-bind:class="{ selected : isSelected('3') }" @click="onClick('3')" src="./rebirthLuggageImages/Image-3.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('7') }" @click="onClick('7')" src="./rebirthLuggageImages/Image-7.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('11') }" @click="onClick('11')" src="./rebirthLuggageImages/Image-11.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('15') }" @click="onClick('15')" src="./rebirthLuggageImages/Image-15.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('19') }" @click="onClick('19')" src="./rebirthLuggageImages/Image-19.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('24') }" @click="onClick('24')" src="./rebirthLuggageImages/Image-24.png" alt="" /></td>
                        </tr>
                        <tr>
                            <td><img v-bind:class="{ selected : isSelected('4') }" @click="onClick('4')" src="./rebirthLuggageImages/Image-4.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('8') }" @click="onClick('8')" src="./rebirthLuggageImages/Image-8.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('12') }" @click="onClick('12')" src="./rebirthLuggageImages/Image-12.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('16') }" @click="onClick('16')" src="./rebirthLuggageImages/Image-16.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('20') }" @click="onClick('20')" src="./rebirthLuggageImages/Image-20.png" alt="" /></td>
                            <td><img v-bind:class="{ selected : isSelected('25') }" @click="onClick('25')" src="./rebirthLuggageImages/Image-25.png" alt="" /></td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <div id="locationImages" class="location-images">
                <div v-if="displayLocationImage1" id="locationImagePosition1">
                    <img class="location-image" v-bind:class="{ selected: isSelectedImagePosition('1')}" :src="locationImage1" @click="zoomImage(locationImage1)" alt="" />
                    <h3>{{ '(' + (locationImage1.split('/')[locationImage1.split('/').length - 1]).substr(0, 2) + ') ' + (locationImage1.split(' - ')[locationImage1.split(' - ').length - 2]) }}</h3>
                    <h3>{{ (locationImage1.split(' - ')[locationImage1.split(' - ').length - 1]).substr(0, (locationImage1.split(' - ')[locationImage1.split(' - ').length - 1]).indexOf('.')) }}</h3>
                    <!-- <h3>{{ locationImage1.toString().substr(locationImage1.toString().indexOf(' - ') - 2, (locationImage1.toString().substr(locationImage1.indexOf(' - ') - 2)).indexOf('.')) }}</h3> -->
                </div>
                <div v-if="displayLocationImage2" id="locationImagePosition2">
                    <img class="location-image" v-bind:class="{ selected: isSelectedImagePosition('2') }" :src="locationImage2" @click="zoomImage(locationImage2)" alt="" />
                    <h3>{{ '(' + (locationImage2.split('/')[locationImage2.split('/').length - 1]).substr(0, 2) + ') ' + (locationImage2.split(' - ')[locationImage2.split(' - ').length - 2]) }}</h3>
                    <h3>{{ (locationImage2.split(' - ')[locationImage2.split(' - ').length - 1]).substr(0, (locationImage2.split(' - ')[locationImage2.split(' - ').length - 1]).indexOf('.')) }}</h3>
                    <!-- <h3>{{ locationImage2.toString().substr(locationImage2.toString().indexOf(' - ') - 2, (locationImage2.toString().substr(locationImage2.indexOf(' - ') - 2)).indexOf('.')) }}</h3> -->
                </div>
                <div v-if="displayLocationImage3" id="locationImagePosition3">
                    <img class="location-image" v-bind:class="{ selected: isSelectedImagePosition('3') }" :src="locationImage3" @click="zoomImage(locationImage3)" alt="" />
                    <h3>{{ '(' + (locationImage3.split('/')[locationImage3.split('/').length - 1]).substr(0, 2) + ') ' + (locationImage3.split(' - ')[locationImage3.split(' - ').length - 2]) }}</h3>
                    <h3>{{ (locationImage3.split(' - ')[locationImage3.split(' - ').length - 1]).substr(0, (locationImage3.split(' - ')[locationImage3.split(' - ').length - 1]).indexOf('.')) }}</h3>
                    <!-- <h3>{{ locationImage3.toString().substr(locationImage3.toString().indexOf(' - ') - 2, (locationImage3.toString().substr(locationImage3.indexOf(' - ') - 2)).indexOf('.')) }}</h3> -->
                </div>
            </div>
        </div>

        <div id="key-pad" v-if="displayKeypad">
            <div>
             <KeyPad />
            </div>
        </div>

        <div class="reset-images">
            <button class="key" @click="reset()">Reset Images</button>
        </div>

    </div>

</template>

<script>
import { ref } from 'vue'
import './RebirthLuggageImages.css'
import KeyPad from './KeyPad.vue'
import VueEasyLightbox from 'vue-easy-lightbox'
// import VueEasyLightboxComponent from './VueEasyLightbox.vue'

import RebirthLocationImage01 from './rebirthLuggageLocationImages/01 - Security - Underneath Ramp At Security Comm Tower.jpg'
import RebirthLocationImage02 from './rebirthLuggageLocationImages/02 - Prison Reception - Underneath Staircase.jpg'
import RebirthLocationImage03 from './rebirthLuggageLocationImages/03 - 2nd Floor Decon - Above Circuit Breakers.jpg'
import RebirthLocationImage04 from './rebirthLuggageLocationImages/04 - Gondola - Top Gondola.jpg'
import RebirthLocationImage05 from './rebirthLuggageLocationImages/05 - Shipping And Receiving - Behind Front Filing Cabinets.jpg'
import RebirthLocationImage06 from './rebirthLuggageLocationImages/06 - Bio - 3rd Floor (By Periodic Chart).jpg'
import RebirthLocationImage07 from './rebirthLuggageLocationImages/07 - 2nd Floor Cells - Lockers.jpg'
import RebirthLocationImage08 from './rebirthLuggageLocationImages/08 - 2nd Floor Chem - Under stairs.jpg'
import RebirthLocationImage09 from './rebirthLuggageLocationImages/09 - Shack Outside Construction - By Ladder.jpg'
import RebirthLocationImage10 from './rebirthLuggageLocationImages/10 - Harbor - Pipes Outside.jpg'
import RebirthLocationImage11 from './rebirthLuggageLocationImages/11 - Red Roof - Outside Behind Boxes.jpg'
import RebirthLocationImage12 from './rebirthLuggageLocationImages/12 - Comunication Office - Behind Ceiling Extention.jpg'
import RebirthLocationImage13 from './rebirthLuggageLocationImages/13 - Living Quarters - Top Room Bottom Bookshelf.jpg'
import RebirthLocationImage14 from './rebirthLuggageLocationImages/14 - 2nd Floor Chem - Under Desk Near Window.jpg'
import RebirthLocationImage15 from './rebirthLuggageLocationImages/15 - 2nd Building At Living Quarters Row - Bottom Windowless Room Above Bookshelf.jpg'
import RebirthLocationImage16 from './rebirthLuggageLocationImages/16 - Outside Construction Sheds - Under Zip (Behind Barrels).jpg'
import RebirthLocationImage17 from './rebirthLuggageLocationImages/17 - Nova Factory Watchtower - 3rd Floor (On Ceiling).jpg'
import RebirthLocationImage18 from './rebirthLuggageLocationImages/18 - Middle Of Chem Tunnel - Above Bodies.jpg'
import RebirthLocationImage19 from './rebirthLuggageLocationImages/19 - Inside Tunnel To Prison - Behind Power Unit.jpg'
import RebirthLocationImage20 from './rebirthLuggageLocationImages/20 - 2nd Floor Decon - Behind TV By Buy.jpg'
// import RebirthLocationImage21 from './rebirthLuggageLocationImages/21 - Old Construction - Cement Mixer.jpg'
import RebirthLocationImage22 from './rebirthLuggageLocationImages/22 - Decon - Behind Crates Outside Stairs.jpg'
import RebirthLocationImage23 from './rebirthLuggageLocationImages/23 - Security Shack - Under Table.jpg'
import RebirthLocationImage24 from './rebirthLuggageLocationImages/24 - Living Quarter Row - Outside Parachute Above Air Conditioner.jpg'
import RebirthLocationImage25 from './rebirthLuggageLocationImages/25 - Nova - Middle Room (Behind Top Monitors).jpg'
import RebirthLocationImage26 from './rebirthLuggageLocationImages/26 - Bio - Basement Piping Cubby.jpg'

export default {
    components: {
        VueEasyLightbox,
        KeyPad
    },
    data() {
        return {
            imgs: [],
            visible: false,
            index: 0, // default: 0
            selectedImages: [],
            keyCode1: '',
            keyCode2: '',
            keyCode3: '',
            locationImage1: '',
            locationImage2: '',
            locationImage3: '',
            displayLocationImage1: [],
            displayLocationImage2: [],
            displayLocationImage3: [],
            displayKeypad: [],
            displayImages: [],
            selectedPosition: null,
            locationImage1Open: [],
            locationImage2Open: [],
            locationImage3Open: []
        }
    },
    mounted() {
        // let imgs = ref('')
        // let visible = ref()
        // let index = ref()
        // let imgs = [{ title: 'abcd', src: 'http://via.placeholder.com/350x150' }]

        // imgs = []
        // imgs = [{ title: 'abcd', src: 'http://via.placeholder.com/350x150' }]
        // visible.value = true
        // index = 0

        // let keyCode1 = ref()
        // let keyCode2 = ref()
        // let keyCode3 = ref()

        // let locationImage1 = ref()
        // let locationImage2 = ref()
        // let locationImage3 = ref()

        // let displayLocationImage1 = ref('')
        // let displayLocationImage2 = ref('')
        // let displayLocationImage3 = ref('')

        this.displayLocationImage1 = false
        this.displayLocationImage2 = false
        this.displayLocationImage3 = false

        // let displayKeypad = ref('')
        this.displayKeypad = false

        // let displayImages = ref('')
        this.displayImages = true

        // let selectedPosition = null

        // let locationImage1Open = true
        // let locationImage2Open = true
        // let locationImage3Open = true

        // let selectedImages = []
    },
    methods: {
        zoomImage(imageSource) {
            const title = (imageSource.toString().substr(imageSource.toString().indexOf(' - ') - 2, (imageSource.toString().substr(imageSource.indexOf(' - ') - 2)).indexOf('.')))

            this.imgs = [{ 
                title: title,
                src: imageSource.toString()
            }]
            this.show()
        },
        onClick(imageNumber) {
            if (this.selectedImages.filter(x => x.id === imageNumber).length > 0) {
                return;
            }

            let currentlySelectedImages = this.selectedImages;
            

            // no position is selected and all three image positions are filled
            if (this.selectedPosition === null && !this.locationImage1Open && !this.locationImage2Open && !this.locationImage3Open) {
                return
                // this.selectedPosition = 3
            }

            //if (this.selectedPosition !== null || (this.selectedPosition === null && selectedImages.filter(x => x.id === imageNumber)).length === 0) {
                let locationImageSource = '';
                let locationImage = ''
                switch(imageNumber) {
                    case "1": 
                        locationImageSource = RebirthLocationImage01
                        locationImage = 'src/components/rebirthLuggageLocationImages/01 - Underneath Ramp At Security Comm Tower.jpg'
                        break
                    case "2":
                        locationImageSource = RebirthLocationImage02
                        locationImage = "src/components/rebirthLuggageLocationImages/02 - Prison Reception - Underneath Staircase.jpg"
                        break
                    case "3":
                        locationImageSource = RebirthLocationImage03
                        locationImage = "src/components/rebirthLuggageLocationImages/03 - 2nd Floor Decon - Above Circuit Breakers.jpg"
                        break
                    case "4":
                        locationImageSource = RebirthLocationImage04
                        locationImage = "src/components/rebirthLuggageLocationImages/04 - Top Gondola.jpg"
                        break
                    case "5":
                        locationImageSource = RebirthLocationImage05
                        locationImage = "src/components/rebirthLuggageLocationImages/05 - Shipping And Receiving - Behind Front Filing Cabinets.jpg"
                        break
                    case "6":
                        locationImageSource = RebirthLocationImage06
                        locationImage = "src/components/rebirthLuggageLocationImages/06 - Bio - 3rd Floor - By Periodic Chart.jpg"
                        break
                    case "7":
                        locationImageSource = RebirthLocationImage07
                        locationImage = "src/components/rebirthLuggageLocationImages/07 - 2nd Floor Cells - Lockers.jpg"
                        break
                    case "8":
                        locationImageSource = RebirthLocationImage08
                        locationImage = "src/components/rebirthLuggageLocationImages/08 - 2nd Floor Chem - Under stairs.jpg"
                        break
                    case "9":
                        locationImageSource = RebirthLocationImage09
                        locationImage = "src/components/rebirthLuggageLocationImages/09 - Shack Outside Construction - By Ladder.jpg"
                        break
                    case "10":
                        locationImageSource = RebirthLocationImage10
                        locationImage = "src/components/rebirthLuggageLocationImages/10 - Harbor - Pipes Outside.jpg"
                        break
                    case "11":
                        locationImageSource = RebirthLocationImage11
                        locationImage = "src/components/rebirthLuggageLocationImages/11 - Red Roof - Outside Behind Boxes.jpg"
                        break
                    case "12":
                        locationImageSource = RebirthLocationImage12
                        locationImage = "src/components/rebirthLuggageLocationImages/12 - Comunication Office - Behind Ceiling Extention.jpg"
                        break
                    case "13":
                        locationImageSource = RebirthLocationImage13
                        locationImage = "src/components/rebirthLuggageLocationImages/13 - Living Quarters - Top Room Bottom Bookshelf.jpg"
                        break
                    case "14":
                        locationImageSource = RebirthLocationImage14
                        locationImage = "src/components/rebirthLuggageLocationImages/14 - 2nd Floor Chem - Under Desk Near Window.jpg"
                        break
                    case "15":
                        locationImageSource = RebirthLocationImage15
                        locationImage = "src/components/rebirthLuggageLocationImages/15 - 2nd Building At Living Quarters Row - Bottom Windowless Room Above Bookshelf.jpg"
                        break
                    case "16":
                        locationImageSource = RebirthLocationImage16
                        locationImage = "src/components/rebirthLuggageLocationImages/16 - Outside Construction Sheds - Under Zip - Behind Barrels.jpg"
                        break
                    case "17":
                        locationImageSource = RebirthLocationImage17
                        locationImage = "src/components/rebirthLuggageLocationImages/17 - Nova Factory Watchtower - 3rd Floor - On Ceiling.jpg"
                        break
                    case "18":
                        locationImageSource = RebirthLocationImage18
                        locationImage = "src/components/rebirthLuggageLocationImages/18 - Middle Of Chem Tunnel - Above Bodies.jpg"
                        break
                    case "19":
                        locationImageSource = RebirthLocationImage19
                        locationImage = "src/components/rebirthLuggageLocationImages/19 - Inside Tunnel To Prison - Behind Power Unit.jpg"
                        break
                    case "20":
                        locationImageSource = RebirthLocationImage20
                        locationImage = "src/components/rebirthLuggageLocationImages/20 - 2nd Floor Decon - Behing TV By Buy.jpg"
                        break
                    case "21":
                        locationImageSource = RebirthLocationImage21
                        locationImage = "src/components/rebirthLuggageLocationImages/21 - Old Construction - Cement Mixer.jpg"
                        break
                    case "22":
                        locationImageSource = RebirthLocationImage22
                        locationImage = "src/components/rebirthLuggageLocationImages/22 - Decon - Behind Crates Outside Stairs.jpg"
                        break
                    case "23":
                        locationImageSource = RebirthLocationImage23
                        locationImage = "src/components/rebirthLuggageLocationImages/23 - Security Shack - Under Table.jpg"
                        break
                    case "24":
                        locationImageSource = RebirthLocationImage24
                        locationImage = "24 - Living Quarter Row - Outside Parachute Above Air Conditioner.jpg"
                        break
                    case "25":
                        locationImageSource = RebirthLocationImage25
                        locationImage = "25 - Nova - Middle Room - Behind Top Monitors.jpg"
                        break
                    case "26":
                        locationImageSource = RebirthLocationImage26
                        locationImage = "26 - Bio - Basement Piping Cubby.jpg"
                        break
                    default:
                        locationImageSource = ''
                        locationImage = ''
                }

                if (this.selectedPosition === 1 || (this.selectedPosition === null && this.locationImage1Open)) {
                    if (!this.locationImage1Open) {
                        currentlySelectedImages = currentlySelectedImages.filter(x => x.value !== locationImage1.value);
                    }
                    this.locationImage1 = locationImageSource
                    this.displayLocationImage1 = true
                    this.locationImage1Open = false
                    
                } else if ((this.selectedPosition !== null && this.selectedPosition <= 2) || (this.selectedPosition === null && this.locationImage2Open)) {
                    if (!this.locationImage2Open) {
                        currentlySelectedImages = currentlySelectedImages.filter(x => x.value !== this.locationImage2.value);
                    }
                    this.locationImage2 = locationImageSource
                    this.displayLocationImage2 = true
                    this.locationImage2Open = false
                } else if ((this.selectedPosition !== null && this.selectedPosition <= 3) || (this.selectedPosition === null && this.locationImage3Open)) {
                    if (!this.locationImage3Open) {
                        currentlySelectedImages = currentlySelectedImages.filter(x => x.value !== this.locationImage3.value);
                    }
                    this.locationImage3 = locationImageSource
                    this.displayLocationImage3 = true
                    this.locationImage3Open = false
                }

                if (this.locationImage1Open === false && this.locationImage2Open === false && this.locationImage3Open === false) {
                    this.displayKeypad = true
                }

                this.selectedImages = [];

                this.selectedImages.push({ "id": imageNumber, "value": locationImageSource });

                if (currentlySelectedImages.length > 0) {
                    currentlySelectedImages.forEach(x => { this.selectedImages.push(x) });
                }

                this.selectedPosition = null;
            //}
            
        },
        selectPosition(position) {
            debugger
            // this.selectedPosition = position
        },
        isSelected(imageNumber) {
            if (this.selectedImages.length != 0) {
                return this.selectedImages.filter(x => x.id === imageNumber) != 0
            }
            return false
        },
        isSelectedImagePosition(imagePosition) {
            if (this.selectedPosition != null) {
                return imagePosition === this.selectedPosition
            }
            return false
        },
        reset() {
            this.selectedPosition = null
            this.locationImage1 = ''
            this.locationImage2 = ''
            this.locationImage3 = ''

            this.locationImage1Open = true
            this.locationImage2Open = true
            this.locationImage3Open = true
            
            this.displayLocationImage1 = false
            this.displayLocationImage2 = false
            this.displayLocationImage3 = false

            this.displayKeypad = false

            this.selectedImages = []

            this.resetKeyCode()
        },
        resetKeyCode() {
            this.keyCode1 = ''
            this.keyCode2 = ''
            this.keyCode3 = ''
        },
        numberOnly(event) {
            event.target.value = event.target.value.replace(/[^0-9]/gi, "")
        },
        show() {
            this.visible = true
        },
        handleHide() {
            this.visible = false
        },
    },
}

</script>

