<script>
export default {
    props: {
        show: Boolean,
        painting: Object
    }
}
</script>

<template>
  <Transition name="modal">
    <div v-if="show" @click="$emit('close')" class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container" @click.stop>
          <div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              <div class="carousel-item active">
                <img :src="painting.path" class="d-block w-100">
              </div>
              <div class="carousel-item" v-for="path in painting.pics">
                <img :src="path" class="d-block w-100">
              </div>
            </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Next</span>
            </button>
          </div>
          <div class="describe">
            <div class="title_author">
              <span class="title_painting">«{{painting.title}}»</span>
              <span class="name_author">{{painting.author}}</span>
              <p>{{painting.describe}}</p>
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
                <span id="sales" v-if="!painting.price">Продана на аукционе</span>
              </div>
              <MyButton @click="$emit('close')">OK</MyButton>
            </div>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 500px;
  height: auto;
  margin: 0px auto;
  background-color: #F6F3F3;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

@media screen and (max-width: 600px) {
  .modal-container {
    max-width: 500px;
    width: auto;
    margin: 0 30px;
  }
}

.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

.describe {
  padding: 20px 24px 24px 24px;
  height: 100%;
}

.describe p {
  margin-top: 10px;
  text-align: justify;
}

.title_author {
  display: flex;
  flex-direction: column;
  margin-bottom: 22px;
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