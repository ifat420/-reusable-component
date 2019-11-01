<template>
    <button
        class="i-btn"
        ref="btn"
        @click.prevent="onClick"
        :class="{ 'btn-gry': btnGry, 'btn-blu': btnBlu }"
    >{{btnText}}</button>
</template>

<script>
export default {
    props: {
        btnText: {
            type: String,
            required: true
        },

        btnGry: {
            type: Boolean,
            default: false
        },

        btnBlu: {
            type: Boolean,
            default: false
        }
    },

    methods: {
        onClick(e) {
            let btn = this.$refs.btn;
            let X = e.pageX - btn.offsetLeft;
            let Y = e.pageY - btn.offsetTop;

            let rippleDiv = document.createElement("div");
            rippleDiv.classList.add("ripple");
            rippleDiv.setAttribute(
                "style",
                "top:" + Y + "px; left:" + X + "px;"
            );

            btn.appendChild(rippleDiv);

            setTimeout(() => {
                rippleDiv.parentElement.removeChild(rippleDiv);
            }, 900);
        }
    }
};
</script>

<style lang="scss" scoped>
.i-btn {
    position: relative;
    overflow: hidden;
    padding: 15px 32px;
    border: none;
    outline: none;
    background: var(--primary-color);
    color: var(--white-color);
    font-size: 1.6rem;
    font-family: var(--btn-font);
    text-transform: uppercase;
    cursor: pointer;
    margin: 10px;
    transition: all 0.2s ease;
    box-shadow: 0 3px 1px -2px rgba(0, 0, 0, 0.2),
        0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12);

    &:hover {
        background: lighten(#f07070, 10);
    }

    &:active {
        outline: none;
    }
}

.btn-gry {
    background: var(--grey-color-3);

    &:hover {
        background: lighten(#90a4ae, 10);
    }
}

.btn-blu {
    background: var(--secondary-color);

    &:hover {
        background: lighten(#468fbd, 10);
    }
}

%rpl {
    position: absolute;
    width: 5px;
    height: 5px;
    border-radius: 50%;
    opacity: 0;
    animation: rippleEffect 0.88s 1;
}

.ripple {
    @extend %rpl;
    background: #fff;
}

.ripple-drk {
    @extend %rpl;
    background: rgba(0, 0, 0, 0.87);
}
</style>