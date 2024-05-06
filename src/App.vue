
<template>

<div class="container">
    <header>
        <img alt="JEEC logo" class="logo" src="./assets/jeec-logo.svg" height="60px" />
    </header>

    <Carousel :items-to-show="1.5" :wrap-around="true">
        <Slide v-for="slide in slides" :key="slide">
            <div class="carousel__item">
                <p v-if=slide.text class="Question">{{slide.content}}</p>
                <img v-if=slide.img alt="Web dev logo" class="webdev_logo" v-bind:src=slide.content width="100%">
                <VueDatePicker v-if=slide.input class="date" v-model="date" model-type="dd.MM.yyyy" auto-apply placeholder="Select Date" />
                <div class="texto">
                    <h1 v-if=slide.flex>Intergration of wind farms into Eletricity </h1>
                    <h1 v-if=slide.flex>Grids</h1>
                    <h2 v-if=slide.flex>Workshop</h2>
                    <h3 v-if=slide.flex>By Vestas</h3>
                    <p v-if=slide.flex> This workshop will cover the representation of wind solution in simulation software, with an emphasis on wind turbine design and eletrical performance for compliance with grid requirements.</p>
                    <p v-if=slide.flex>  </p> 
                    <p v-if=slide.flex>  </p>
                    <p v-if=slide.flex></p>
                </div>
                
            </div>
        </Slide>

        <template #addons>
            <Navigation />
            <Pagination />
        </template>

    </Carousel>
    <div class="answers">
        <h3>A resposta é não faço puto ideia!</h3>
        <h3>{{date}}</h3>
    </div>
    
    
</div>


</template>

<script>
import challenge from "./assets/challenge.png"
import Background from "./assets/jeec-2.jpg"
import {
    Carousel,
    Navigation,
    Pagination,
    Slide,
} from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'
import VueDatePicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css'
import {
    ref
} from 'vue';

const date = ref();





export default {
  name: 'App',
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
    VueDatePicker,
  },
  setup() {
    const date = ref();

    return {
      date
    }
    },
  data () {
    return{
        slides:[
        {id: '1', title: 'Question', content: 'Qual a melhor frase do film do shrek?', img: false, text: true, input: false, flex:false},
        {id: '2', title: 'Date', content: date, img: false, text: false, input: true, flex:false},
        {id: '3', title: 'flexbox', content: 'Rendering Conditionally', img: false, text: false, input: false, flex:true},
        {id: '4', title: 'img', content: challenge, img: true, text: false, input: false, flex:false},
        ]
    }
  }
}

</script>

<style scoped>

.container {
    display: flex;
    flex-direction: column;
    /* Stack elements vertically */
    align-items: center;
    /* Option A for vertical centering */
    justify-content: center;
    max-width: 95vw;
    min-height: 80vh;

}

.carousel {
    min-width: 93vw;
    max-height: 1000px;
    
}

.carousel__track {
    box-sizing: border-box;
}

.carousel__item {
    margin-block: 10px;
    max-height: 500px;
    max-width: 800px;
    border-radius: 8px;
    font-size: 40px;
    background-color: var(--vt-c-black-soft);
}
.Question{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-items: center;
    padding: 100px;
}
.date{
    padding: 100px;
}

.texto{
    display: flex;
    flex-direction: column;
    /* Stack elements vertically */
    align-items: flex-start;
    /* Option A for vertical centering */
    justify-items: flex-start;
    font-size:27px;
    text-align: left;
    padding: 20px;
}

.webdev_logo {
    display: flex;
    justify-items: center;
    width: 800px;
    padding: 20px;
    align-items: center;
    background-color: var(--vt-c-black);
    
}


.carousel__slide {
    padding: 4px;
}

.carousel__prev,
.carousel__next {
    color: #000;
    box-sizing: border-box;
    border: 4px solid white;
}
</style>
