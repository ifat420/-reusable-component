<template>
    <div class="radio">
        <label :for="furniture.id" class="radio__label">
            {{furniture.name }}
            <input
                :id="furniture.id"
                :value="$t(furniture.name)"
                v-model="formData.interest"
                class="radio__input"
                type="checkbox"
            />
            <span class="radio__mark"></span>
        </label>
    </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.radio {
    display: block;
    margin-bottom: 10px;
    padding-left: 15px;
    &__label {
        position: relative;
        display: block;
        padding-left: 30px;
        cursor: pointer;
        font-size: 16px;
    }

    &__text {
        font-size: 16px;
        margin-bottom: 10px;
    }

    &__mark {
        position: absolute;
        width: 20px;
        height: 20px;
        // background: red;
        border: 1px solid #000;
        top: 0;
        left: 0;
        border-radius: 100%;
        box-shadow: $box-shadow-1;
        transition: all 0.25s ease;
    }

    &__input {
        position: absolute;
        opacity: 0;
    }

    &__input:checked + &__mark {
        background: #000;
        box-shadow: inset 0 0 0 4px #fff;
    }
}
</style>