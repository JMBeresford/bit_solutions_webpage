<template>
  <b-container id="wrapperContainer" fluid>
    <b-row id="header">
      <img height="80px" src="../assets/bit_solutions.png">
    </b-row>
    <b-container id="contentContainer">
      <b-row v-if="!underConstruction" id="links">
        <b-button v-b-tooltip.hover title="Under Construction..." disabled variant="outline-secondary">
          About Us
        </b-button>
        <b-button v-b-tooltip.hover title="Under Construction..." disabled variant="outline-secondary">
          Previous Work
        </b-button>
      </b-row>
      <b-row>
        <b-col lg="8" class="contentCol">
          <b-row id="carousels" no-gutters>
            <div>
              <b-carousel id="carouselImg" fade @sliding-start="changeSlide">
                <b-carousel-slide img-src="../assets/consult.jpg" />
                <b-carousel-slide img-src="../assets/web-dev.jpg" />
                <b-carousel-slide img-src="../assets/commercial.jpg" />
              </b-carousel>
            </div>
            <div id="carouselText">
              <transition name="fade">
                <p v-if="slideNo == 0" class="slideText">
                  Consultancy with an emphasis on clear lines of communication
                </p>
              </transition>
              <transition name="fade">
                <p v-if="slideNo == 1" class="slideText">
                  Website design and developmental services
                </p>
              </transition>
              <transition name="fade">
                <p v-if="slideNo == 2" class="slideText">
                  Commercial computer systems and network servicing
                </p>
              </transition>
            </div>
          </b-row>
        </b-col>
        <b-col id="ctaCol" class="contentCol">
          <div id="ctaWrapper">
            <p id="callToActionText">
              Contact Us for a Consultation
            </p>
            <b-button id="ctaBtn" v-b-modal.consultModal>
              Get a Consultation
            </b-button>
          </div>
        </b-col>
      </b-row>
    </b-container>
    <b-modal id="consultModal" ok-only hide-footer title="">
      <b-row>
        <b-col class="contactCol">
          <h5>
            Call Us:
          </h5>
          <p>
            (760) 799-3498
          </p>
        </b-col>
        <b-col class="contactCol">
          <h5>
            Email Us:
          </h5>
          <b-link href="mailto:john@beresford.tech">
            john@beresford.tech
          </b-link>
        </b-col>
      </b-row>
    </b-modal>
  </b-container>
</template>

<script>
export default {
  data () {
    return {
      slideNo: 0,
      underConstruction: true
    }
  },
  computed: {
    textSize () {
      return 2
    }
  },
  methods: {
    changeSlide (slide) {
      this.slideNo = slide
    }
  }
}
</script>

<style>
:root {
  --black: #000000ff;
  --oxford-blue: #14213dff;
  --orange-web: #fca311ff;
  --platinum: #e5e5e5ff;
  --white: #ffffffff;
}
.fade-enter-active, .fade-leave-active {
  transition: all 0.75s ease;
}
.fade-enter-to, .fade-leave {
  opacity: 1;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
body {
  background-color: var(--platinum);
}
#header {
  background-color: var(--oxford-blue);
  justify-content: center;
}
#contentContainer {
  height: 100%;
  padding-bottom: 1em;
}
#links {
  padding-top: 1em;
  padding-bottom: 1em;
  display: flex;
  justify-content: center;
}
#links > * {
  margin: 0 1em;
  padding: 5px 7px;
}
hr.rule {
  border-top: rgba(0,0,0,0.45) solid 1px;
}
#carousels {
  position: relative;
  height: 100%;
  width: 100%;
}
#carouselText {
  z-index: 1000;
  background-color: rgba(0, 0, 0, 0.75);
  position: absolute;
  width: 100%;
  height: 100%;
  display: grid;
}
.slideText {
  color: white;
  font-size: 1.5em;
  font-weight: bold;
  margin: auto;
  padding: 0 10px;
  text-align: center;
  grid-row: 1;
  grid-column: 1;
}
.contentCol {
  padding: 0;
}
#ctaCol {
  display: flex;
  background-color: white;
  text-align: center;
  width: 100%;
  height: inherit;
  align-items: center;
}
#ctaWrapper {
  width: 100%;
  padding: 1em 0;
}
#callToActionText {
  font-size: 1.5em;
}
#ctaBtn {
  background-color: var(--oxford-blue);
  padding: 1em;
  font-size: 1em;
}
#ctaBtn:hover {
  background-color: var(--orange-web);
  color: black;
}
.headerBtn:hover {
  background-color: var(--oxford-blue);
  color: var(--platinum);
}
.contactCol {
  padding: 1em 0;
  text-align: center;
}
</style>
