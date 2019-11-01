<template>
    <div class="textarea">
        <p class="order__text">{{$t('Your message here:')}}</p>
        <textarea
            v-model="formData.message"
            class="textarea--area"
            name="message"
            id
            rows="10"
        ></textarea>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
.textarea {
    &--area {
      width: 100%;
      resize: none;
      border: 1px solid $color-black;
      padding: 1rem;
      font-size: 16px;
      font-family: $font-1;
      &:focus {
        outline: none;
      }
    }
  }
</style>