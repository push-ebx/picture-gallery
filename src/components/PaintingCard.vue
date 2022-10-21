<template>
  <div class="card" :class="{opacity: !painting.price}">
    <img 
      :src="painting.path" 
      alt="" 
      @click="showModal = true"
    >
    <div class="describe">
      <div class="title_author">
        <span class="title_painting">«{{painting.title}}»</span>
        <span class="name_author">{{painting.author}}</span>
      </div>
      <div class="button_price">
        <div class="prices">
          <span v-if="painting.old_price">
            <strike class="strike_price">
              {{painting.old_price.toLocaleString().split(',').join(' ')}} $
            </strike>
          </span>
          <span id="main_price" v-if="painting.price">
            {{painting.price.toLocaleString().split(',').join(' ')}} $
          </span>
        </div>
        <MyButton 
          @click="handleClickButton" 
          v-if="painting.price" 
          :in_basket="this.check"
          class="btn-buy"
        >
          <div v-if="is_loading" class="spinner-border spinner-border-sm text-light" role="status">
            <span class="visually-hidden">Loading...</span>
          </div>
          {{is_loading ? "Обработка" : (in_basket() ? "В корзине" : "Купить")}}
        </MyButton>
      </div>
      <span id="sales" v-if="!painting.price">Продана на аукционе</span>
    </div>
  </div>
  <Teleport to="body">
    <modal 
      :show="showModal"
      @close="showModal = false"
      :painting="painting"
    />
  </Teleport>
</template>
<script>
import Modal from './Modal.vue'

export default {
  components: { 
    Modal
  },
  props: {
    painting: {
      type: Object,
      required: true
    }
  },
  methods: {
    addInBasket(id) {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          localStorage[id] = true
          resolve()
        }, 2000)
      })
    },
    removeOfBasket(id) {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          localStorage.removeItem(id)
          resolve()
        }, 2000)
      })
    },
    handleClickButton(event) {
      if (this.is_loading) return
      if (this.in_basket()) {
        this.is_loading = true
        this.check = false
        this.removeOfBasket(this.painting.id).then(() => {this.is_loading = false})
      } else {
        this.is_loading = true
        this.addInBasket(this.painting.id).then(() => {this.is_loading = false})
      }
    },
    in_basket() {
      this.check = localStorage[this.painting.id]
      return this.check
    }
  },
  data() {
    return {
      is_loading: false,
      check: false,
      showModal: false
    }
  },
}
</script>
<style scoped>
  .card {
    border: 1px solid #e1e1e1;
    border-radius: 0px;
    background-color: #F6F3F3;
    min-width: 280px;
    max-width: 280px;
  }

  .card img:hover {
    cursor: pointer;
  }

  .describe {
    padding: 20px 24px 24px 24px;
    height: 100%;
  }

  .title_author {
    display: flex;
    flex-direction: column;
    margin-bottom: 22px;
  }

  .title_author:hover {
    cursor: pointer;
  }

  .title_author span {
    font-weight: 400;
    font-size: 18px;
  }

  .prices {
    display: flex;
    flex-direction: column;
    font-weight: 700;
  }

  .strike_price {
    color: #A0A0A0;
    font-size: 14px;
  }

  #main_price {
    color: #343030;
    font-size: 16px;
  }

  #sales {
    display: block;
    margin-top: 10px;
    font-size: 16px;
    font-weight: 700;
  }

  .opacity {
    opacity: 0.5;
  }

  .button_price {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>