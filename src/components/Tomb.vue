<template>
    <div class="tomb" :title="ShortInfo">
        <img v-if="tomb.logo" class="tomb__logo" :src="'img/logos/'+tomb.logo" alt="logo">
        <img v-else class="tomb__logo" src="img/def_logo.svg" alt="logo">
        <p class="tomb__title tomb__name">{{ tomb.name }}</p>
        <p class="tomb__title tomb__years">{{ tomb.year_start }}-{{ tomb.year_end }}</p>
        <div class="tomb__flowers" @click="$emit('addLike', tomb)" :title="tomb.likes">
            <img class="tomb__flowers__item" v-if="tomb.likes < 10" v-for="n in tomb.likes" :key="n" src="img/flower.png" alt="flowers">
            <img v-else class="tomb__flowers__many" src="img/flowers.png" alt="flowers">
        </div>
        <!-- <my-dialog v-model:show="tombDetails">
          <tomb-id-info :tombId="" />
        </my-dialog> -->

    </div>
  </template>
  
  <script>
  export default {
    props: {
      tomb: {
        type: Object,
        required: true,
      }
    },
    computed: {
        ShortInfo() {
          return this.tomb.name + ' (' + this.tomb.year_start + '-' + this.tomb.year_end + ')'
        },
    },
    methods: {
    }
  }
  </script>
  
  <style scoped>
  .tomb {
    background-image: url("../../public/img/tomb.png");
    background-repeat: no-repeat;
    height: 150px;
    width: 125px;
    padding: 10px 20px 20px 25px;
    justify-content: center;
    overflow: hidden;
    /* border: white 1px solid; */
  }

  .tomb__logo {
    height: 25px;
    display: flex;
    margin: 0px auto;
    border-radius: 20px;
    border: gray solid 1px;
    /* opacity: 50%; */

  }

  .tomb__flowers__item:nth-child(odd) {
    /* transform: rotate(-10deg); */
  }
  .tomb__flowers__item:nth-child(even) {
    /* transform: rotate(10deg); */

  }
  .tomb__flowers {
    height: 25px;
    justify-content: center;
    display: flex;
    padding: 0px 5px;
    cursor: grab;
    /* overflow: hidden; */
    /* margin: 5px auto; */
  }
  .tomb__title {
    padding: 5px;
    color: white;
    text-align: center;
    cursor: zoom-in;
       
  }
  .tomb__name {
    height: 40px;
    font-size: 0.8em;
    /* margin-left: 5px; */
  }

  .tomb__years {
    height: 25px;
    font-size: 0.8em;
  }


  </style>
  