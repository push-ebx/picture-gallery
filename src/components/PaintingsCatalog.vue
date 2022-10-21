<template>
  <div class="catalog">
    <h1 class="title_catalog">{{catalog.title_catalog}}</h1>
    <div class="cards" v-if="catalog.paintings.length">
      <PaintingCard
        v-for="painting in catalog.paintings"
        :painting="painting"
      />
    </div>
    <h3 :style="{marginTop: '20px'}" v-else>По данному запросу картины не найдены</h3>
  </div>
</template>
<script>
import PaintingCard from "./PaintingCard.vue";
export default {
  components: {
    PaintingCard
  },
  props: {
    catalog: {
      type: Object,
      required: true
    }
  } 
}
</script>
<style scoped>
  .catalog {
    display: flex;
    flex-direction: column;
  }
  
  .title_catalog {
    font-weight: 700;
    font-size: 24px;
  }
  
  .cards {
    display: flex;
    max-width: 1216px;
    flex-wrap: wrap;
    gap: 32px;
    margin-top: 39px;
  }

  @media screen and (max-width: 1250px) {
    .cards{
      max-width: 940px;
      column-gap: 50px;
    }
  }

  @media screen and (max-width: 950px) {
    .cards{
      max-width: 580px;
      column-gap: 20px;
    }
  }

  @media screen and (max-width: 600px) {
    .catalog {
      max-width: 280px;
    }
  }
</style>