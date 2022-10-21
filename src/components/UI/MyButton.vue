<template>
  <button 
  class="my-btn" 
  :disabled="is_disabled"
  :class="{disabled: is_disabled, basket: in_basket}"
  >
    <img v-if="in_basket" src="/assets/check.svg" alt=""><slot></slot>
  </button>
</template>
<script>
export default {
  name: 'MyButton',
  props: {
    is_disabled: {type: Boolean},
    in_basket: {type: Boolean}
  }
}
</script>
<style>
  .my-btn {
    background-color: #403432;
    color: #F4F6F9;
    font-size: 14px;
    font-weight: 700;
    border: none;
    max-width: 120px;
    width: 100%;
    min-height: 48px;
  }

  .my-btn img {
    margin: 0 3px 3px;
  }
  
  .my-btn:hover:enabled {
    background-color: #776763;
  }

  .basket {
    background-color: #5B3A32;
  }

  .disabled {
    background-color: #C1B4B1;
  }
</style>