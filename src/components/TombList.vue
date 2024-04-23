<template>

  <div v-if="tombs.length > 0">
    <div class="tomb-list">
      <tomb v-for="tomb in tombs" :tomb="tomb" :key="tomb.id" @addLike="$emit('addLike', tomb)" />
    </div>
  </div>  
  <h2 v-else style="color: red">
      Пусто
  </h2>
  
</template>

<script>
import Tomb from "@/components/Tomb";
export default {
  components: { Tomb },
  props: {
    tombs: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

.tomb-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  justify-items: center;
  row-gap: 20px;
}

@media screen and (max-width: 1200px) {
}

</style>