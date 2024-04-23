<template>
  <div class="app">
    <div class="grid-container">
      <navbar></navbar>
      <div class="main">
        <div class="entrance-table">
          <h1 class="table-h1">Кладбище <br>компаний</h1>
        </div>
        <tomb-list :tombs="sortedAndSearchedTombs" @addLike="addLike" v-if="!isTombsLoading" />
        <div v-else>Идет загрузка...</div>
        <div v-intersection="loadMoreTombs" class="observer"></div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar";
import TombList from "@/components/TombList";
import MyButton from "@/components/UI/MyButton";
import axios from 'axios';
import MySelect from "@/components/UI/MySelect";
import MyInput from "@/components/UI/MyInput";

export default {
  components: {
    Navbar,
    MyInput,
    MySelect,
    MyButton,
    TombList
  },
  data() {
    return {
      tombs: [],
      dialogVisible: false,
      isTombsLoading: false,
      selectedSort: '',
      searchQuery: '',
      page: 1,
      limit: 70,
      totalPages: 0,
      sortOptions: [
        {value: 'title', name: 'По названию'},
        {value: 'body', name: 'По содержимому'},
      ]
    }
  },
  methods: {
    createTomb(tomb) {
      this.tombs.push(tomb);
      this.dialogVisible = false;
    },
    removeTomb(tomb) {
      this.tombs = this.tombs.filter(p => p.id !== tomb.id)
    },
    addLike(tomb) {
      tomb.likes++;
    },
    showDialog() {
      this.dialogVisible = true;
    },
    fetchTombs() {
      fetch('data.json')
      .then(response => {
        return response.json();
      })
      .then(data => {
        this.tombs = data;
      })
      .catch(error => {
        console.error('Ошибка загрузки файла:', error);
      });
    },
    async fetchTombsO() {
      try {
        this.isTombsLoading = true;
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
          params: {
            _page: this.page,
            _limit: this.limit
          }
        });
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
        this.tombs = response.data;
      } catch (e) {
        alert('Ошибка')
      } finally {
        this.isTombsLoading = false;
      }
    },
    async loadMoreTombs() {
      try {
        this.page += 1;
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
          params: {
            _page: this.page,
            _limit: this.limit
          }
        });
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
        this.tombs = [...this.tombs, ...response.data];
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.fetchTombs();
  },
  computed: {
    // sortedTombs() {
    //   return [...this.tombs].sort((tomb1, tomb2) => tomb1[this.selectedSort]?.localeCompare(tomb2[this.selectedSort]))
    // },
    sortedAndSearchedTombs() {
      return this.tombs
      // return this.sortedTombs.filter(tomb => tomb.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
    }
  },
  watch: {
    // page() {
    //   this.fetchTombs()
    // }
  }
}
</script>

<style>
.grid-container {
  display: grid;
  grid-template-columns: 240px 1fr;
  min-width: 100%;
}

.main {
    background-image: url(../public/img/bg_loan.jpeg);
    background-repeat: repeat;
  }

.entrance-table {
    width: 70%;
    /* height: auto; */
    margin: 20px auto;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 3px solid;
    border-color: black;
    border-radius: 20px;
    background-image: url(../public/img/bg_wood.jpg);
    background-size: cover;
}
  
.table-h1 {
    opacity: 100%;  
    color: white;
    -webkit-text-stroke: 1px black; /* Цвет обводки и толщина обводки */
    font-size: 5em;
}

.observer {
  height: 30px;
  background: green;
}

.app {
  margin: 0px;
}
</style>
