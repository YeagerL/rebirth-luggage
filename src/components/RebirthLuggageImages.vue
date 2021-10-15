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

        <!-- <div id="topRow"> -->
        <div id="topButtons" align="right">
            <div>
                <button id="keypad-toggle" class="key toggle" @click="this.displayKeypad = !this.displayKeypad">Keypad</button>
            </div>

            <div>
                <button class="key toggle" @click="toggleDisplayLuggageLocations" v-bind:class="{ toggleoff : this.displayLuggageLocations }">Luggage Locations</button>
                <!-- <button class="key toggle" v-if="this.displayLuggageLocations" @click="toggleDisplayLuggageLocations">Hide Luggage Locations</button> -->
            </div>

            <div>
                <button class="key toggle" v-if="!this.displayRebirthImages || this.allPositionsFilled()" @click="this.displayRebirthImages = !this.displayRebirthImages">
                    {{ !this.displayRebirthImages ? 'Show' : 'Hide' }} Luggage Pictures
                </button>
            </div>

            <div>
                <button class="key key-round" @click="(this.togglegif = !this.togglegif)" v-bind:class="{ toggleoff : this.togglegif }"></button>  
                <div>
                    gif {{ this.togglegif ? 'off' : 'on' }}
                </div>
            </div>
        </div>
        <!-- </div> -->

        <div id="images">
            <div id="luggage-locations" v-if="displayLuggageLocations">
                <!-- <img @click="zoomImage('../components/rebirthLuggageImages/LuggageLocations.jpg')" src="../components/rebirthLuggageImages/LuggageLocations.jpg" alt="" /> -->
                <!-- <img src="../components/rebirthLuggageImages/RebirthIslandMapLargeLuggageLocations.jpg" alt="" /> -->
                <img :src="luggageLocationsImage" @click="zoomImage(luggageLocationsImage)" alt="" />
            </div>

            <div v-if="displayRebirthImages">
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
                <div v-if="(this.selectedLocationImages !== undefined && this.selectedLocationImages[0].value !== '')" id="locationImagePosition1">
                    <img class="location-image" v-bind:class="{ selected: isSelectedImagePosition('1')}" :src="!this.togglegif && selectedLocationImages[0].video.length > 0 ? selectedLocationImages[0].video : selectedLocationImages[0].value" @click="zoomImage(selectedLocationImages[0])" alt="" />
                    <h3>{{ this.buildImageTitle(0) }}</h3>
                    <h3>{{ this.buildImageDescription(0) }}</h3>
                </div>
                <div v-if="(this.selectedLocationImages !== undefined && this.selectedLocationImages[1].value !== '')" id="locationImagePosition2">
                    <img class="location-image" v-bind:class="{ selected: isSelectedImagePosition('2') }" :src="!this.togglegif && selectedLocationImages[1].video.length > 0 ? selectedLocationImages[1].video : selectedLocationImages[1].value" @click="zoomImage(selectedLocationImages[1])" alt="" />
                    <h3>{{ this.buildImageTitle(1) }}</h3>
                    <h3>{{ this.buildImageDescription(1) }}</h3>
                </div>
                <div v-if="(this.selectedLocationImages !== undefined && this.selectedLocationImages[2].value !== '')" id="locationImagePosition3">
                    <img class="location-image" v-bind:class="{ selected: isSelectedImagePosition('3') }" :src="!this.togglegif && selectedLocationImages[2].video.length > 0 ? selectedLocationImages[2].video : selectedLocationImages[2].value" @click="zoomImage(selectedLocationImages[2])" alt="" />
                    <h3>{{ this.buildImageTitle(2) }}</h3>
                    <h3>{{ this.buildImageDescription(2) }}</h3>
                </div>
            </div>

            <div id="key-pad" v-if="displayKeypad">
                <div>
                    <KeyPad />
                </div>
            </div>
            
            <div class="reset-images" v-if="(this.selectedLocationImages.find(x => x.value.length > 0) !== undefined)">
                <button class="key" @click="reset()">Reset Images</button>
            </div>

            
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
  import RebirthLocationVideo01 from './rebirthLuggageLocationImages/01 - Security - Underneath Ramp At Security Comm Tower.gif'

  import RebirthLocationImage02 from './rebirthLuggageLocationImages/02 - Prison Reception - Underneath Staircase.jpg'
  import RebirthLocationVideo02 from './rebirthLuggageLocationImages/02 - Prison Reception - Underneath Staircase.gif'

  import RebirthLocationImage03 from './rebirthLuggageLocationImages/03 - Decon 2nd Floor - Above Circuit Breakers.jpg'
  import RebirthLocationVideo03 from './rebirthLuggageLocationImages/03 - Decon 2nd Floor - Above Circuit Breakers.gif'

  import RebirthLocationImage04 from './rebirthLuggageLocationImages/04 - Gondola - Top Gondola.jpg'
  import RebirthLocationVideo04 from './rebirthLuggageLocationImages/04 - Gondola - Top Gondola.gif'

  import RebirthLocationImage05 from './rebirthLuggageLocationImages/05 - Shipping And Receiving - Behind Front Filing Cabinets.jpg'
  import RebirthLocationVideo05 from './rebirthLuggageLocationImages/05 - Shipping And Receiving - Behind Front Filing Cabinets.gif'

  import RebirthLocationImage06 from './rebirthLuggageLocationImages/06 - Bio - 3rd Floor By Periodic Chart.jpg'
  import RebirthLocationVideo06 from './rebirthLuggageLocationImages/06 - Bio - 3rd Floor By Periodic Chart.gif'

  import RebirthLocationImage07 from './rebirthLuggageLocationImages/07 - Cells - 2nd Floor Lockers.jpg'
  import RebirthLocationVideo07 from './rebirthLuggageLocationImages/07 - Cells - 2nd Floor Lockers.gif'

  import RebirthLocationImage08 from './rebirthLuggageLocationImages/08 - Chem - 2nd Floor Under stairs Behind Pipe.jpg'
  import RebirthLocationVideo08 from './rebirthLuggageLocationImages/08 - Chem - 2nd Floor Under stairs Behind Pipe.gif'

  import RebirthLocationImage09 from './rebirthLuggageLocationImages/09 - Shack Outside Control - By Ladder.png'
  import RebirthLocationVideo09 from './rebirthLuggageLocationImages/09 - Shack Outside Control - By Ladder.gif'

  import RebirthLocationImage10 from './rebirthLuggageLocationImages/10 - Harbor - Pipes Outside.png'
  import RebirthLocationVideo10 from './rebirthLuggageLocationImages/10 - Harbor - Pipes Outside.gif'

  import RebirthLocationImage11 from './rebirthLuggageLocationImages/11 - Red Roof - Outside Behind Boxes.jpg'
  import RebirthLocationVideo11 from './rebirthLuggageLocationImages/11 - Red Roof - Outside Behind Boxes.gif'

  import RebirthLocationImage12 from './rebirthLuggageLocationImages/12 - Communication Office - Behind Ceiling Extention (Bottom floor).jpg'
  import RebirthLocationVideo12 from './rebirthLuggageLocationImages/12 - Communication Office - Behind Ceiling Extention (Bottom floor).gif'

  import RebirthLocationImage13 from './rebirthLuggageLocationImages/13 - Living Quarters - Top Room Bottom Bookshelf.jpg'
  import RebirthLocationVideo13 from './rebirthLuggageLocationImages/13 - Living Quarters - Top Room Bottom Bookshelf.gif'

  import RebirthLocationImage14 from './rebirthLuggageLocationImages/14 - Chem 4th Floor - Under Desk Near Window.jpg'
  import RebirthLocationVideo14 from './rebirthLuggageLocationImages/14 - Chem 4th Floor - Under Desk Near Window.gif'

  import RebirthLocationImage15 from './rebirthLuggageLocationImages/15 - 2nd Building At Living Quarters Row - Bottom Windowless Room Above Bookshelf.jpg'
  import RebirthLocationVideo15 from './rebirthLuggageLocationImages/15 - 2nd Building At Living Quarters Row - Bottom Windowless Room Above Bookshelf.gif'

  import RebirthLocationImage16 from './rebirthLuggageLocationImages/16 - Outside Control Sheds - Under Zip Behind Barrels.jpg'
  import RebirthLocationVideo16 from './rebirthLuggageLocationImages/16 - Outside Control Sheds - Under Zip Behind Barrels.gif'

  import RebirthLocationImage17 from './rebirthLuggageLocationImages/17 - Nova Factory Watchtower - 3rd Floor On Ceiling.jpg'
  import RebirthLocationVideo17 from './rebirthLuggageLocationImages/17 - Nova Factory Watchtower - 3rd Floor On Ceiling.gif'

  import RebirthLocationImage18 from './rebirthLuggageLocationImages/18 - Middle Of Chem Tunnel - Above Bodies.jpg'
  import RebirthLocationVideo18 from './rebirthLuggageLocationImages/18 - Middle Of Chem Tunnel - Above Bodies.gif'

  import RebirthLocationImage19 from './rebirthLuggageLocationImages/19 - Inside Tunnel To Prison - Behind Power Unit.jpg'
  import RebirthLocationVideo19 from './rebirthLuggageLocationImages/19 - Inside Tunnel To Prison - Behind Power Unit.gif'

  import RebirthLocationImage20 from './rebirthLuggageLocationImages/20 - Decon 2nd Floor - Behind TV By Buy.jpg'
  import RebirthLocationVideo20 from './rebirthLuggageLocationImages/20 - Decon 2nd Floor - Behind TV By Buy.gif'

  import RebirthLocationImage22 from './rebirthLuggageLocationImages/22 - Decon - Behind Crates Outside Stairs.jpg'
  import RebirthLocationVideo22 from './rebirthLuggageLocationImages/22 - Decon - Behind Crates Outside Stairs.gif'

  import RebirthLocationImage23 from './rebirthLuggageLocationImages/23 - Security Shack - Under Table.jpg'
  import RebirthLocationVideo23 from './rebirthLuggageLocationImages/23 - Security Shack - Under Table.gif'

  import RebirthLocationImage24 from './rebirthLuggageLocationImages/24 - Living Quarter Row - Outside Parachute Above Air Conditioner.jpg'
  import RebirthLocationVideo24 from './rebirthLuggageLocationImages/24 - Living Quarter Row - Outside Parachute Above Air Conditioner.gif'

  import RebirthLocationImage25 from './rebirthLuggageLocationImages/25 - Nova - Middle Room Behind Top Monitors.jpg'
  import RebirthLocationVideo25 from './rebirthLuggageLocationImages/25 - Nova - Middle Room Behind Top Monitors.gif'

  import RebirthIslandMapLargeLuggageLocations from './rebirthLuggageImages/RebirthIslandMapLargeLuggageLocations.jpg'

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
        displayKeypad: false,
        displayImages: [],
        displayLuggageLocations: false,
        displayRebirthImages: [],
        selectedPosition: null,
        selectedLocationImages: [
          { id: 0, value: '' },
          { id: 0, value: '' },
          { id: 0, value: '' }
        ],
        togglegif: false,
        luggageLocationsImage: ''
      }
    },
    mounted() {
      this.displayKeypad = false

      this.displayImages = true
      this.displayLuggageLocations = false
      this.displayRebirthImages = true

      this.selectedLocationImages = [
        { id: 0, value: '' },
        { id: 0, value: '' },
        { id: 0, value: '' }
      ]

      this.luggageLocationsImage = RebirthIslandMapLargeLuggageLocations
    },
    methods: {
      toggleDisplayLuggageLocations() {
        this.displayLuggageLocations = !this.displayLuggageLocations
      },
      buildImageTitle(imageIndex) {
        if (this.selectedLocationImages[imageIndex] === undefined) {
          return
        }
        const image = this.selectedLocationImages[imageIndex].value
        const imageTitle = image === undefined ? '' : '(' + (image.split('/')[image.split('/').length - 1]).substr(0, 2) + ') ' + (image.split(' - ')[image.split(' - ').length - 2])
        return imageTitle
      },
      buildImageDescription(imageIndex) {
        if (this.selectedLocationImages[imageIndex] === undefined) {
          return
        }

        const image = this.selectedLocationImages[imageIndex].value
        const description = image === undefined ? '' : (image.split(' - ')[image.split(' - ').length - 1]).substr(0, (image.split(' - ')[image.split(' - ').length - 1]).indexOf('.'))
        return description
      },
      zoomImage(image, title = null) {
        const imageSource = image.value ?? image

        if (title === null) {
          title = (imageSource.toString().substr(imageSource.toString().indexOf(' - ') - 2, (imageSource.toString().substr(imageSource.indexOf(' - ') - 2)).indexOf('.')))
        }

        let images = [];
        if (!this.togglegif && image.video !== undefined && image.video.length > 0) {
          images.push({
            title: title,
            src: image.video.toString()
          })
        }

        images.push({
          title: title,
          src: imageSource.toString(),
        })

        this.imgs = images
        this.show()
      },
      allPositionsFilled() {
        return (this.selectedLocationImages !== undefined && (this.selectedLocationImages.find(x => x.value === '') === undefined))
      },
      onClick(imageNumber) {
        debugger
        if (this.selectedImages.filter(x => x.id === imageNumber).length > 0) {
          return;
        }

        let currentlySelectedImages = this.selectedImages;

        // no position is selected and all three image positions are filled
        if (this.selectedPosition === null && this.allPositionsFilled()) {
          return
          // this.selectedPosition = 3
        }

        //if (this.selectedPosition !== null || (this.selectedPosition === null && selectedImages.filter(x => x.id === imageNumber)).length === 0) {
        let locationImageSource = ''
        let locationVideoSource = ''
        switch (imageNumber) {
          case "1":
            locationImageSource = RebirthLocationImage01
            locationVideoSource = RebirthLocationVideo01
            break
          case "2":
            locationImageSource = RebirthLocationImage02
            locationVideoSource = RebirthLocationVideo02
            break
          case "3":
            locationImageSource = RebirthLocationImage03
            locationVideoSource = RebirthLocationVideo03
            break
          case "4":
            locationImageSource = RebirthLocationImage04
            locationVideoSource = RebirthLocationVideo04
            break
          case "5":
            locationImageSource = RebirthLocationImage05
            locationVideoSource = RebirthLocationVideo05
            break
          case "6":
            locationImageSource = RebirthLocationImage06
            locationVideoSource = RebirthLocationVideo06
            break
          case "7":
            locationImageSource = RebirthLocationImage07
            locationVideoSource = RebirthLocationVideo07
            break
          case "8":
            locationImageSource = RebirthLocationImage08
            locationVideoSource = RebirthLocationVideo08
            break
          case "9":
            locationImageSource = RebirthLocationImage09
            locationVideoSource = RebirthLocationVideo09
            break
          case "10":
            locationImageSource = RebirthLocationImage10
            locationVideoSource = RebirthLocationVideo10
            break
          case "11":
            locationImageSource = RebirthLocationImage11
            locationVideoSource = RebirthLocationVideo11
            break
          case "12":
            locationImageSource = RebirthLocationImage12
            locationVideoSource = RebirthLocationVideo12
            break
          case "13":
            locationImageSource = RebirthLocationImage13
            locationVideoSource = RebirthLocationVideo13
            break
          case "14":
            locationImageSource = RebirthLocationImage14
            locationVideoSource = RebirthLocationVideo14
            break
          case "15":
            locationImageSource = RebirthLocationImage15
            locationVideoSource = RebirthLocationVideo15
            break
          case "16":
            locationImageSource = RebirthLocationImage16
            locationVideoSource = RebirthLocationVideo16
            break
          case "17":
            locationImageSource = RebirthLocationImage17
            locationVideoSource = RebirthLocationVideo17
            break
          case "18":
            locationImageSource = RebirthLocationImage18
            locationVideoSource = RebirthLocationVideo18
            break
          case "19":
            locationImageSource = RebirthLocationImage19
            locationVideoSource = RebirthLocationVideo19
            break
          case "20":
            locationImageSource = RebirthLocationImage20
            locationVideoSource = RebirthLocationVideo20
            break
          case "22":
            locationImageSource = RebirthLocationImage22
            locationVideoSource = RebirthLocationVideo22
            break
          case "23":
            locationImageSource = RebirthLocationImage23
            locationVideoSource = RebirthLocationVideo23
            break
          case "24":
            locationImageSource = RebirthLocationImage24
            locationVideoSource = RebirthLocationVideo24
            break
          case "25":
            locationImageSource = RebirthLocationImage25
            locationVideoSource = RebirthLocationVideo25
            break
          default:
            locationImageSource = ''
            locationVideoSource = ''
        }

        let selectedPositionIndex = this.getSelectedPositionIndex()
        if (this.selectedLocationImages[selectedPositionIndex].value !== '') {
          currentlySelectedImages = currentlySelectedImages.filter(x => x.value !== this.selectedLocationImages[selectedPositionIndex].value)
        }
        this.selectedLocationImages[selectedPositionIndex].value = locationImageSource
        this.selectedLocationImages[selectedPositionIndex].video = locationVideoSource

        if (this.selectedLocationImages !== undefined && this.allPositionsFilled()) {
          this.displayKeypad = true
          this.displayRebirthImages = false
        }

        this.selectedImages = [];

        this.selectedImages.push({ "id": imageNumber, "value": locationImageSource });

        if (currentlySelectedImages.length > 0) {
          currentlySelectedImages.forEach(x => { this.selectedImages.push(x) });
        }

        // this.selectedLocationImages = this.selectedImages

        this.selectedPosition = null;
        //}

      },
      getSelectedPositionIndex() {
        if (this.selectedPosition === 1 || (this.selectedPosition === null && this.selectedLocationImages[0].value === '')) {
          return 0
        }

        if ((this.selectedPosition !== null && this.selectedPosition <= 2) || (this.selectedPosition === null && this.selectedLocationImages[1].value === '')) {
          return 1
        }

        if ((this.selectedPosition !== null && this.selectedPosition <= 3) || (this.selectedPosition === null && this.selectedLocationImages[2].value === '')) {
          return 2
        }
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
      resetImages() {
        this.selectedPosition = null
        this.locationImage1 = ''
        this.locationImage2 = ''
        this.locationImage3 = ''
      },
      reset() {
        this.resetImages()

        this.displayKeypad = false
        this.displayRebirthImages = true
        this.displayLuggageLocations = false
        this.selectedImages = []

        this.selectedLocationImages = [
          { id: 0, value: '' },
          { id: 0, value: '' },
          { id: 0, value: '' }
        ]

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

