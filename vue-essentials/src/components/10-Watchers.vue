<script>
    export default {
        data() {
            return {
                question: '',
                answer: 'Questions usually contain a question mark. ;-)',
                loading: false,
                newQuestion: '',
                someObject: {}
            }
        },
        watch: {
            // 每当 question 改变时，这个函数就会执行
            question(newQuestion, oldQuestion) {
                if (newQuestion.includes('?')) {
                    this.getAnswer()
                }
            },
            // 深层侦听器
            someObject: {
                handler(newValue, oldValue) {
                    // 注意：在嵌套的变更中，
                    // 只要没有替换对象本身，
                    // 那么这里的 `newValue` 和 `oldValue` 相同
                },
                deep: true
            },
            // 即时回调的侦听器
            question: {
                handler(newQuestion) {
                    // 在组件实例创建时会立即调用
                },
                // 强制立即执行回调
                immediate: true
            },
            // 想在侦听器回调中能访问被 Vue 更新之后的 DOM，你需要指明 flush: 'post' 选项
            key: {
                handler() {},
                flush: 'post'
            }
        },
        // 使用组件实例的 $watch() 方法来命令式地创建一个侦听器
        created() {
            this.$watch('question', (newQuestion) => {
            // ...
            })
        },
        methods: {
            async getAnswer() {
                this.loading = true
                this.answer = 'Thinking...'
                try {
                    const res = await fetch('https://yesno.wtf/api')
                    this.answer = (await res.json()).answer
                } catch (error) {
                    this.answer = 'Error! Could not reach the API. ' + error
                } finally {
                    this.loading = false
                }
            },
            // 停止侦听器
            unwatch() {
                const unwatch = this.$watch('foo', callback)

                // ...当该侦听器不再需要时
                unwatch()
            }
        }
}

</script>




<template>

    <h1>侦听器</h1>

    <hr>
    <h3>基本示例</h3>
    <p>
        Ask a yes/no question:
        <input v-model="question" :disabled="loading" />
    </p>
    <p>{{ answer }}</p>


    <hr>
    <h3>深层侦听器</h3>


    <hr>
    <h3>即时回调的侦听器</h3>


    <hr>
    <h3>回调的触发时机</h3>


    <hr>
    <h3>this.$watch()</h3>


    <hr>
    <h3>停止侦听器</h3>
    


</template>