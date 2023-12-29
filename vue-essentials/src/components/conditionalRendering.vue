<script>

    export default {
        data() {
            return {
                awesome: true,
                type: 'E',
                ok: true
            }
        }
    }

</script>




<template>

    <h1>条件渲染</h1>

    <hr>
    <h3>v-if     v-else     v-else-if</h3>
    <button @click="awesome = !awesome">Toggle</button>
    <h1 v-if="awesome">Vue is awesome!</h1>
    <h1 v-else>Oh no 😢</h1>


    <div v-if="type === 'A'">
    A
    </div>
    <div v-else-if="type === 'B'">
    B
    </div>
    <div v-else-if="type === 'C'">
    C
    </div>
    <div v-else>
    Not A/B/C
    </div>


    <hr>
    <h3>if  template</h3>
    <template v-if="ok">
        <h1>Title</h1>
        <p>Paragraph 1</p>
        <p>Paragraph 2</p>
    </template>


    <hr>
    <h3>v-show</h3>
    <!-- v-show 仅切换了该元素上名为 display 的 CSS 属性。 -->
    <!-- v-show 不支持在 <template> 元素上使用 -->
    <h1 v-show="ok">Hello!</h1>



</template>