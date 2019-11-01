<template>
  <div class="input-text">
    <label :for="id" class="input-text__label">{{label}}</label>
    <input 
      :id="id" 
      :value="value" 
      @input="$emit('input',$event.target.value)" 
      class="input-text__input" 
      type="text">
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    id: String,
    value: String
  }
}
</script>

<style lang="scss" scoped>
.input-text {
  width: 100%;
  margin-bottom: 1rem;

  &__label {
    display: block;
    font-family: $font-1;
    font-size: 16px;
    padding: .5rem 1rem .5rem 1rem;
    color: $color-black;
  }

  &__input {
    padding: 1rem;
    border: 1px solid $color-black;
    color: $color-black;
    display: block;
    width: 100%;
    font-size: 16px;
    font-family: $font-1;
    &:focus {
      outline: none;
    }
  }
}

</style>