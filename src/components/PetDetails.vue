<template>
  <div id="petDetails">
    <div class="errors" v-if="errors.length">
      <h2 v-for="error of errors">{{ error.message }}</h2>
    </div>
    <div id="swiper-wrapper">
    <swiper :options="swiperOption">
      <swiper-slide style="background-image:url(http://lorempixel.com/1000/500/)" v-for="n in 10" :key="n">
       <div class="slide-content" @click="openModal"></div>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
      <div class="swiper-button-prev" slot="button-prev"></div>
      <div class="swiper-button-next" slot="button-next"></div>
    </swiper>
    </div>
    <Modal v-if="showModal" @close="showModal = false" class="modal"></Modal>
    <div class="petInfo">
      <ul class="list-group pet-ul">
        <li class="pet-li">
            <img class="float-left-span" src="../assets/circle-outline.png">
            <div class="center-span float-left-span">
              <span>{{$route.params.name}}</span>
              <span class="li-span-name">{{$t('pets.name')}}</span>
            </div>
        </li>
        <li class="pet-li">
          <img class="float-left-span" src="../assets/jack-russell-terrier.png">
          <div class="name-wrapper float-left-span">
            <span>{{$route.params.type}}</span>
            <span class="center-span li-span-dog">{{$t('pets.type')}}</span>
          </div>
          <div class="sex-wrapper">
            <img class="float-left-span float-right-span" src="../assets/gender.png">
            <span class="center-span">{{$route.params.sex}}</span>
            <span class="center-span li-span-sex">{{$t('pets.sex')}}</span>
          </div>
        </li>
        <li class=" pet-li">
          <img class="float-left-span" src="../assets/calendar.png">
          <div class="float-left-span center-span">
            <span>{{$route.params.created}}</span>
            <span class="li-span-calendar center-span">{{$t('pets.creationDate')}}</span>
          </div>
        </li>
      </ul>
    </div>
    <h2>{{$route.params.description}}</h2>
  </div>
</template>
<script>
  import { swiper, swiperSlide } from 'vue-awesome-swiper'
  export default {
    data () {
      return {
        errors: [],
        swiperOption: {
          nextButton: '.swiper-button-next',
          prevButton: '.swiper-button-prev',
          pagination: '.swiper-pagination',
          paginationType: 'fraction'
        },
        showModal: false
      }
    },
    components: {
      swiper,
      swiperSlide
    },
    methods: {
      openModal () {
        this.showModal = true
      }
    }
  }
</script>
<style>
  #petDetails{
    margin-top: 10%;
  }
  .petInfo{
    margin-left: 20%;
    width: 60%;
    display: block;
  }
  .pet-ul{
    width: 100%;
    border-top: 0;
    padding: 0;
    margin: 3.0em 0 3.0em 0 ;
    list-style-type: none;
  }
  .pet-li{
    width: 100%;
    padding: 10px;
    border: 0;
    border-bottom: 1px solid lightgray;
    font:22px arial,sans-serif;
    font-weight: bold;
    display: flex;
    flex-direction: row;
  }
  .sex-wrapper{
    width: 50%;
    float:right;
    margin-left: 13vw;
  }
  .center-span{
    flex-direction: column;
    display: flex;
    text-align: left;
  }
  .li-span-dog{
    font-size: 14px;
    color: gray;
    margin-top: 1.5em;
  }
  .li-span-sex{
    font-size: 14px;
    color: gray;
    margin-top: 1.5em;
    margin-right: 2.0em;
  }
  .li-span-name{
    font-size: 14px;
    color: gray;
    margin-top: 1.5em;
    float: left;
  }
  .li-span-calendar{
    font-size: 14px;
    color: gray;
    margin-top: 1.5em;
  }
  .float-left-span{
    float:left;
    margin-left: 5px;
  }
  .slide-content{
    width: 700px;
    height: 350px;
    margin: 0 auto;
  }
  .swiper-slide {
    background-position: center;
    background-size: cover;
  }
  .swiper-pagination{
    color:#fff;
    font: 18px arial, sans-serif;
  }
  #swiper-wrapper{
    width: 60%;
    margin: 0 0 0 20%;
  }
/* MEDIA QUERIES */
  @media only screen and (max-width: 450px){
    #swiper-wrapper{
      width: 90%;
      margin: 0 auto;
    }
    .slide-content{
      width: 700px;
      height: 250px;
      margin: 0 auto;
    }
    .petInfo{
      margin: 0 auto;
      width: 90%;
      display: block;
    }
    .pet-li{
      width: 100%;
      padding: 10px;
      border: 0;
      border-bottom: 1px solid lightgray;
      font:14px arial,sans-serif;
      font-weight: bold;
    }
    .pet-ul{
      margin: 1.0em 0 1.0em 0 ;
      list-style-type: none;
    }
    .float-right-span{
      margin-left:30% ;
    }
    .sex-wrapper{
      width: 40vw;
    }
  }

</style>