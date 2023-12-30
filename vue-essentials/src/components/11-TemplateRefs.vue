<script>

export default {
    data() {
        return {
            list: [
                'qwe', 'asd', 'zxc'
            ]
        }
    },
    mounted() {
        this.$refs.input.focus()

        console.log(this.$refs.items)
    }
}
</script>



<template>

    <h1>侦听器</h1>

    <hr>
    <h3>访问模板引用</h3>

    <input ref="input" />



    <hr>
    <h3>v-for 中的模板引用</h3>

    <ul>
        <li v-for="item in list" ref="items">
            {{ item }}
        </li>
    </ul>



    <hr>
    <h3>函数模板引用</h3>

    <input :ref="(el) => { /* 将 el 赋值给一个数据属性或 ref 变量 */ }">



    <hr>
    <h3>组件上的 ref</h3>


</template>