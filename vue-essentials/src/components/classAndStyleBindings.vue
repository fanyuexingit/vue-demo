<script>
    export default {
        data() {
            return {
                isActive: true,
                hasError: false,
                error: null,
                classObject: {
                    active: true,
                    'text-danger': false
                },
                activeClass: 'active',
                errorClass: 'text-danger',
                activeColor: 'red',
                fontSize: 30,
                styleObject: {
                    color: 'red',
                    fontSize: '13px'
                }
            }
        },
        computed: {
            classObject2() {
                return {
                active: this.isActive && !this.error,
                'text-danger': this.error && this.error.type === 'fatal'
                }
            }
        }
    }
</script>



<template>

    <h1>Class 与 Style 绑定</h1>

    <hr>
    <h3>绑定 HTML class</h3>
    <div class="static" :class="{ active: isActive, 'text-danger': hasError }"></div>

    <div :class="classObject"></div>

    <div :class="classObject2"></div>



    <div :class="[activeClass, errorClass]"></div>

    <div :class="[isActive ? activeClass : '', errorClass]"></div>

    <div :class="[{ active: isActive }, errorClass]"></div>



    <!-- 子组件模板 -->
    <p class="foo bar">Hi!</p>
    <!-- 在使用组件时 -->
    <MyComponent class="baz boo" />



    <hr>
    <h3>绑定内联样式</h3>

    <div :style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>

    <div :style="styleObject"></div>

    <div :style="[baseStyles, overridingStyles]"></div>

    <div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>

</template>