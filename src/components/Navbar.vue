<template>
  <!-- Sidebar  -->
  <div class="sidebar">
      <div class="oldman">
          <img width="240" src="img\oldman.png" alt="Смотритель">
      </div>
      <div class="oldmanMessage">Добро пожаловать, <strong>незнакомец</strong>, чего желаешь?</div>
      <div class="navbar">
        <ul class="list-unstyled components">
      <!-- <div @click="$router.push('/')"><strong>Vue 3</strong></div> -->
          <li><my-button @click="showDialog">Что за место?</my-button></li>
          <li><my-button @click="showTombDetails">Представиться</my-button></li>
          <li><my-button @click="$router.push('/store')">Найти</my-button></li>
          <li><my-button @click="$router.push('/composition')">Похоронить</my-button></li>
          <li><my-button @click="$router.push('/composition')">Пожертвовать</my-button></li>
        </ul>
      </div>
      <my-dialog v-model:show="dialogVisible">
        <div class="msgBox">
          Здесь храниться информация о закрывшихся компаниях в стилистике кладбища. Цель проекта - сделать: 
          <ol>
          <li>место медитации - люди могут заходить на кладбище, видеть как много компаний постигло неудачу и черпать из этого силы продолжать свое дело или начинать новое
          </li>
          <li>место памяти - где каждый может “похоронить” свою или понравившуюся компанию, а другие участники могут оставить цветы (а ля “лайк”) в знак памяти
          </li>
        </ol>          
        </div>        
      </my-dialog>
      <my-dialog v-model:show="tombDetails">
        <tomb-id-info :tombId="3" />

      </my-dialog>


  </div>  
</template>

<script>
import MyDialog from "@/components/UI/MyDialog";
import TombIdInfo from "@/components/TombIdInfo";

export default {
  components: {
    MyDialog,
    TombIdInfo
  },
  data() {
    return {
      dialogVisible: false,
      tombDetails: false,
    }
  },
  methods: {
    showDialog() {
      this.dialogVisible = true;

    },
    showTombDetails() {
      this.tombDetails = true;

    },
  }
}
</script>

<style scoped>
.sidebar {
  height: 100vh;
  width: 240px;
  background-color: #1B211F;
  position: sticky;
  top: 0;
  overflow-y: auto;  
  background-image: url(../../public/img/bg_menu.png);
  background-size: cover;
  display: block;
  padding: 0px;
  justify-self: center;

}
.oldmanMessage {
  /* padding: 0px 15px; */
  margin: 15px;
  background-color: teal;
  border: 1px #FD6E07 solid;
  border-radius: 10px;
  color: white;
  text-align: center;
  font-size: 20px;

}

.navbar {
  justify-content: center;
  display: flex;
}

.list-unstyled {
  list-style-type: none; /* Убираем стандартные маркеры у списка ul */

}

.msgBox {
  font-style: oblique;
  font-size: 16px;
}
</style>

