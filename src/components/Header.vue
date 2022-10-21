<template>
  <header>
    <nav class="navbar navbar-expand-lg">
      <div id="nav-bar" class="container">
        <button
          class="navbar-toggler"
          type="button" 
          data-bs-toggle="collapse" 
          data-bs-target="#navbarContent"
          aria-controls="navbarContent"
          aria-expanded="false"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="navbar-nav collapse navbar-collapse" id="navbarContent">
          <div id="wrapper">
            <a href="" class="nav-item">Каталог</a>
            <a href="" class="nav-item">Доставка</a>
            <a href="" class="nav-item">Оплата</a>
            <a href="" class="nav-item">Контакты</a>
            <a href="" class="nav-item">О компании</a>
          </div>
          <div id="search" class="nav-item">
            <input
              type="text"
              placeholder="Поиск по названию картины"
              v-model="searchQuery"
              @keyup.enter="$emit('searching', searchQuery)"
            >
            <MyButton 
              @click="$emit('searching', searchQuery)"
              :style="{padding: '0 36px'}"
            >
              Найти
            </MyButton>
          </div>
        
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: ''
    }
  }
}
</script>

<style scoped>
header {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #F6F3F3;
  border-bottom: 1px solid #e1e1e1;
  padding: 24px;
}

nav {
  width: 100%;
  padding: 0;
}

#navbarContent {
  max-width: 1216px;
}

#wrapper {
  display: flex;
  flex-direction: row;
  justify-content: center;
  width: 100%;
  column-gap: 48px;
}

#nav-bar {
  display: flex;
  justify-content: center;
  width: 100%;
}

#search {
  display: flex;
  height: 48px;
}

#search input {
  height: 100%;
  padding-left: 16px;
  min-width: 290px;
  border-radius: 0;
  outline: none;
  border: 1px solid #E1E1E1;
  border-right: none;
}

#search button {
  height: 100%;
}

@media screen and (max-width: 1200px) {
  #wrapper {
    column-gap: 20px;
  }
}

@media screen and (max-width: 940px) {
  .navbarContent {
    max-width: 940px;
  }
}

@media screen and (max-width: 990px) {
  #wrapper {
    margin-top: 10px;
    flex-direction: column;
    align-items: center;
    row-gap: 10px;
  }

  #search {
    display: none;
  }
}

@media screen and (max-width: 440px) {
  #search input {
    max-width: 200px;
    min-width: auto;
    width: auto;
  }
}
</style>