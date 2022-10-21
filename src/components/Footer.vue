<template>
  <footer>
    <div id="wrapper">
      <div id="footer_nav">
        <a href="">Каталог</a>
        <a href="">Доставка</a>
        <a href="">Оплата</a>
        <a href="">Контакты</a>
        <a href="">О компании</a>
      </div>
      <div id="phone_adress">
        <span>
          <img src="/assets/phone.svg" alt="">
          +7 (812) 555-55-55
        </span>
        <span>
          <img src="/assets/addres.svg" alt="">
          г. Санкт-Петербург, ул. Ефимова, 3
        </span>
      </div>
    </div>
  </footer>
</template>

<style scoped>
  footer {
    display: flex;
    flex-direction: row;
    height: 96px;
    background-color: #ECEAEA;
  }

  #wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
  }

  #footer_nav {
    display: flex;
    margin-right: 127px;
    justify-content: center;
    align-items: center;
    column-gap: 48px;
    height: 100%;
  }

  #phone_adress {
    display: flex;
    justify-content: center;
    column-gap: 54px;
  }

  #phone_adress span img {
    margin-right: 11px;
  }

  @media screen and (max-width: 1200px) {
    footer {
      height: 150px;
      justify-content: center;
      align-items: center;
    }

    #phone_adress {
      flex-direction: column;
      row-gap: 5px;
      height: auto;
    }
    
    #footer_nav {
      flex-direction: column;
      align-items: start;
      row-gap: 5px;
      margin-right: 80px;
      height: auto;
    }
  }

  @media screen and (max-width: 500px) {
    #wrapper {
      flex-direction: column;
      align-items: start;
      row-gap: 20px;
      width: auto;
    }

    #phone_adress {
      align-items: start;
    }

    footer {
      height: 250px;
    }
  }
</style>