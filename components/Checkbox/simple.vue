<template>
    <div class="checkbox">
        <label class="checkbox__label" :for="id">
            {{label}}
            <input
                class="checkbox__input"
                :id="id"
                type="checkbox"
                :checked="value"
                @change="$emit('input', $event.target.checked)"
            />
            <span class="checkbox__mark"></span>
        </label>
    </div>
</template>

<script>
export default {
    props: {
        label: String,
        id: String,
        value: {
            type: Boolean,
            default: false
        }
    }
};
</script>

<style lang="scss" scoped>
.checkbox {
    display: block;
    &__label {
        position: relative;
        display: block;
        padding-left: 30px;
        cursor: pointer;
        font-size: 16px;
    }

    &__mark {
        position: absolute;
        width: 20px;
        height: 20px;
        border: 1px solid #000;
        top: 0;
        left: 0;
        box-shadow: $box-shadow-1;
        transition: all 0.25s ease;
        &:after {
            content: "";
            position: absolute;
            width: 8px;
            height: 13px;
            border: solid #000;
            border-width: 0 2px 2px 0;
            transform: rotate(45deg);
            left: 5px;
            top: -1;
            display: none;
            transition: all 0.25s ease;
            display: none;
        }
    }

    &__input {
        position: absolute;
        opacity: 0;
    }

    &__input:checked ~ &__mark:after {
        display: block;
    }
}
</style>