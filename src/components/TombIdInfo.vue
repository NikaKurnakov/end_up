<template>
  <div class="info-grid-container">
    <div class="leftside">
      <div class="tomb" :title="tomb.title">
          <img class="tomb__logo" src="img/test_logo.png" alt="logo">
          <p class="tomb__title tomb__name">{{ tomb.name }}</p>
          <p class="tomb__title tomb__years">{{ tomb.year_start }}-{{ tomb.year_end }}</p>
          <div class="tomb__flowers">
            <img class="tomb__flowers__item" v-for="n in Math.min(tomb.likes, 10)" :key="n" src="img/flower.png" alt="flowers">
          </div>
      </div>
      <div class="stat">
        <div class="stat__item">
          <img src="img/flower.png" alt="" class="icon"> <div class="number">{{ tomb.likes }}</div>
        </div>
        <div class="stat__item">
          <img src="img/visitors.svg" alt="" class="icon"> <div class="number">{{ tomb.visitors }}</div>
        </div>
      </div>
      <p class="tech-info">Добавлено:<br>{{ tomb.datetime_added }}</p>
      <p v-if="tomb.datetime_added !== tomb.datetime_modified" class="tech-info">Изменено:<br>{{ tomb.datetime_modified }}</p>
    </div>
    <div class="rightside">
      <h2 class="card__name">{{ tomb.name }}</h2>
      <p class="card__alias">({{ tomb.aliases }})</p>
      <h2 class="card__years">{{ tomb.year_start }}-{{ tomb.year_end }}</h2>
      <h3>Жизнь</h3>
      <p class="card__descr">{{ tomb.description_life }}</p>
      <h3>Смерть</h3>
      <p class="card__descr">{{ tomb.description_death }}</p>
      <h3>Характеристики</h3>
      <p class="features">
        <ul>
          <li v-for="(value, key) in tomb.features" :key="key">
            <strong>{{ key }}:</strong> {{ value }}
          </li>
        </ul>
      </p> 

    </div>
  </div>
</template>
  
  <script>
  export default {
    props: {
     tombId: {
        type: Number,
        default: 1
      }

    },
    data() {
      return {
          tomb:    {
            "id": 1,
            "name": "Юниум",
            "year_start": 2000,
            "year_end": 2019,
            "datetime_added": "28.03.2024 0:00:00",
            "datetime_modified": "29.03.2024 0:00:00",
            "user_id": 1,
            "likes": 5,
            "visitors": 6,
            "aliases": "Физтех колледж",
            "description_life": "Юниум – курсы для школьников и абитуриентов\
Более 100 курсов дополнительного образования: творческие, развивающие, школьные предметы.\
📚 Юниум – крупнейшая федеральная образовательная компания, которая была основана в 1991 году и имеет представительство в 9 городах России.\
📚 Более 100 оффлайн курсов в одном месте для детей с 1 по 11 класс.\
🧡Более 40 000 учеников прошли обучение в Юниум и получили персональные сертификаты\
🧡Более 3 500 родителей в год могут с уверенностью утверждать, что их ребенок Любит! Может! Умеет! Учиться",
            "description_death": "Спад продаж в офлайн центрах из-за Covid",
            "features": {
              "official_site": "https://unium.ru/",
              "youtube_channel": "https://www.youtube.com/channel/UCpS399Ed2M6Czsjcz_kRb1g",
              "indusrty": "Школьное дополнительное образование",
              "region": "Россия",
              "founder": "Дмитрий",
              "CEO": "Анатолий",
              "people": "100",
              "revenue_mrub": 20,
              "tags":	"education, russia, offline"
            }
          },
      
      }
    }
  }
  </script>
  
<style scoped>
  .info-grid-container {
    display: grid;
    grid-template-columns: 1fr 2fr;
  }
  .leftside {
    justify-content: center;
  }
  .stat {
    display: flex;
    justify-content: space-around;

  }
  .stat__item {
    display: flex;
    align-items: center;

  }
  .icon {
    height: 25px;
    margin: 3px;
    /* display: flex; */
    
  }
  .number {
    /* display: flex; */
  }
  .rightside {
    justify-content: center;
    margin: 10px;
    padding: 5px;

    /* width: 90%; */
    /* border: 1px solid blue; */
  }
  .card__name {
    text-align: center;
  }
  .card__alias {
    text-align: center;
    font-size: 0.8em;
    font-style: oblique;
    
  }
  .card__years {
    text-align: center;
  }
  .card__descr {
    margin-bottom: 20px;
    padding: 5px;
    /* width: 90%; */
    border: 1px solid gray;
  }
  .features {
    padding: 5px;
    margin-bottom: 10px;
    border: 1px solid gray;
  }

  .features>ul {
    list-style-type: none; /* Убираем стандартные маркеры у списка ul */

  }

  .tech-info {
    font-size: 0.8em;
    font-style: oblique;

  }

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
  }

  .tomb__flowers__item:nth-child(odd) {
    transform: rotate(-10deg);
  }
  .tomb__flowers__item:nth-child(even) {
    transform: rotate(10deg);

  }
  .tomb__flowers {
    height: 25px;
    justify-content: center;
    display: flex;
    padding: 0px 5px;
    cursor: move;
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
  