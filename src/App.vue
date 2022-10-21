<template>
  <Header @searching="query => searchQuery = query"/>
  <main>
    <PaintingsCatalog :catalog="searchedPaintings"/>
  </main>
  <Footer />
</template>

<script>
import Header from "./components/Header.vue"
import PaintingsCatalog from "./components/PaintingsCatalog.vue"
import Footer from "./components/Footer.vue"

export default {
  components: {
    Header,
    PaintingsCatalog,
    Footer
},

  computed: {
    searchedPaintings() {
      return {
        title_catalog: this.catalog.title_catalog,
        paintings: this.catalog.paintings
          .filter(paint => paint.title.toUpperCase().includes(this.searchQuery.toUpperCase()))
          .map(proxy => Object.assign({}, proxy))
      }
    }
  },
  data() {
    return {
      searchQuery: '',
      catalog: {
        title_catalog: "Картины эпохи Возрождения",
        paintings: [
          {
            id: 1,
            title: "Рождение Венеры",
            author: "Сандро Боттичелли",
            old_price: 2000000,
            price: 1000000,
            in_basket: false,
            path: "/assets/painting1.png",
            pics: ["/assets/painting3.png", "/assets/painting4.png"],
            describe: `Картина итальянского художника тосканской школы Сандро Боттичелли. Представляет собой живопись темперой 
            на холсте размером 172,5 x 278,5 см. В настоящее время хранится в галерее Уффици, Флоренция.`
          },
          {
            id: 2,
            title: "Тайная вечеря",
            author: "Леонардо да Винчи",
            old_price: null,
            price: 3000000,
            in_basket: false,
            path: "/assets/painting2.png",
            pics: ["/assets/painting1.png", "/assets/painting3.png"],
            describe: `Монументальная роспись, работа Леонардо да Винчи, изображающая сцену последней трапезы Христа со
             своими учениками. Создана в 1495—1498 годы в доминиканском монастыре Санта-Мария-делле-Грацие в Милане.`
          },
          {
            id: 3,
            title: "Сотворение Адама",
            author: "Микеланджело",
            old_price: 6000000,
            price: 5000000,
            in_basket: true,
            path: "/assets/painting3.png",
            pics: ["/assets/painting1.png", "/assets/painting2.png"],
            describe: `Фреска Микеланджело, написанная около 1511 года. Фреска является четвёртой из девяти центральных 
            композиций потолка Сикстинской капеллы, посвящённых девяти сюжетам книги Бытия. Фреска иллюстрирует эпизод: \"И сотворил Бог человека по образу Своему\"`
          },
          {
            id: 4,
            title: "Урок анатоимии",
            author: "Рембрандт",
            old_price: null,
            price: null,
            in_basket: false,
            path: "/assets/painting4.png",
            pics: ["/assets/painting2.png", "/assets/painting1.png"],
            describe: "Картина Рембрандта, написанная в 1632 году. Центральная фигура картины — доктор Николас Тульп, который показывает собравшимся устройство мускулатуры руки человека."
          }
      ]}
    }
  }
}

</script>

<style> 
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Merriweather';
  font-size: 14px;
  color: #343030;
}

body {
  background-color: #F6F3F3;
}

main {
  display: flex;
  width: 100%;
  justify-content: center;
  padding: 45px 0;
  min-height: calc(100vh - 193px);
}

a {
  text-decoration: none;
  color: #343030;
}

a:visited {
  color: #343030;
}

a:active {
  color: #343030;
}

</style>