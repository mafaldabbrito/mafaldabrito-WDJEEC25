
<template>

<div class="container">
    <header>
        <img alt="JEEC logo" class="logo" src="./assets/jeec-logo.svg" height="80px" />
    </header>

    <Carousel :items-to-show="1.5" :wrap-around="true" :mouseDrag="true" ref="myCarousel">
        <Slide v-for="slide in slides" :key="slide">
            <div class="carousel__item">
                <p v-if=slide.text class="Question">{{slide.content}}</p>
                <img v-if=slide.img alt="Web dev logo" class="webdev_logo" v-bind:src=slide.content>
                <img v-if=slide.shrek alt="Shrek" class="shrek" v-bind:src=slide.content>
                <VueDatePicker v-if=slide.input class="date" v-model="date" model-type="dd.MM.yyyy" auto-apply placeholder="Select Date" />
                <div class="texto">
                    <div class="title">
                        <h1 v-if=slide.flex>Intergration of wind farms into Eletricity Grids</h1>  
                    </div>
                    <div class="sub-title">
                        <h2 v-if=slide.flex>Workshop</h2>
                        <h3 v-if=slide.flex >By Vestas</h3>
                    </div>
                    <p v-if=slide.flex> This workshop will cover the representation of wind solution in simulation software, with an emphasis on wind turbine design and eletrical performance for compliance with grid requirements.</p>
                </div>
                
            </div>
        </Slide>

        <template #addons>
            <Navigation />
            <Pagination />
        </template>

    </Carousel>
    <div class="answers">
        <h3>Oh f*da-se !</h3>
        <h3>Data Selecionada: {{date}}</h3>
    </div>
    
    
</div>


</template>

<script>
import challenge from "./assets/challenge.png"
import shrek from "./assets/shrekdeitado.jpg"
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
import { ref } from 'vue';

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
    const myCarousel= ref(null);
    return {
      date,
      myCarousel,
    };

   
    },
  data () {
    return{
        slides:[
        {id: '1', title: 'Question', content: 'Qual a melhor quote do Shrek? ', img: false, text: true, input: false, flex:false, shrek:false},
        {id: '2', title: 'Date', content: date, img: false, text: false, input: true, flex:false, shrek:false},
        {id: '3', title: 'flexbox', content: 'Rendering Conditionally', img: false, text: false, input: false, flex:true, shrek:false},
        {id: '4', title: 'img', content: challenge, img: true, text: false, input: false, flex:false, shrek:false},
        {id: '5', title: 'shrek', content: shrek, img: false, text: false, input: false, flex:false, shrek:true},
        ],
        
        
        
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
    max-height: 900px;
}

.carousel__track {
    box-sizing: border-box;
}

.carousel__item {
    height: 400px;
    max-width: 900px;
    background-color: var(--vt-c-black-soft);
    border-radius: 20px;
    border: 4px solid #4cc9f0;
    overflow: hidden;
    box-shadow: 0 0 10px #4cc9f0;
}
.Question{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-items: flex-start;
    padding: 100px;
    font-size: 50px;
    font-weight: bold;
}
.date{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-items: center;
    padding: 20px;
  
}



.texto{
    display: flex;
    flex-direction: column;
    /* Stack elements vertically */
    align-items: flex-start;
    /* Option A for vertical centering */
    justify-items: flex-start;
    margin-top: -8px;
    font-size:19px; 
    text-align: left;
    padding: 40px;
  
} 

.title{
    font-weight:bold;
    font-size: 25px;
}

.subtitle{
    padding: 20px;
    text-shadow: 0px 0px 10px #4cc9f0, 2.5px 2.5px 0 #4cc9f0, 2.5px -2.5px 0 #4cc9f0, -2.5px 2.5px 0 #4cc9f0, -2.5px -2.5px 0 #4cc9f0;
}


.shrek {
    display: flex;
    justify-items: center;
    align-items: centers;
    height:400px;
    width:700px;  
}
.webdev_logo {
    display: flex;
    justify-items: center;
    align-items: flex-start;
    max-width: 700px;
    height:400px;
}


.carousel__slide {
    padding: 20px;
}

.carousel__prev,
.carousel__next {
    color: #000;
    box-sizing: border-box;
    border: 4px solid white;
}
.answers{
    padding: 20px;
}
</style>
