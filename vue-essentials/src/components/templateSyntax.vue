<script>
export default {
    data() {
        return {
            msg: 'this is a message demo',
            rawHtml: '<span style="color: red">This should be red.</span>',
            dynamicId: 'xxx',
            isButtonDisabled: true,
            objectOfAttrs: {
                id: 'container',
                class: 'wrapper'
            },
            number: 12,
            ok: true,
            message: 'qwer',
            id: 1,
            date: new Date(),
            seen: true,
            url: 'www.baidu.com',
            attributeName: 'href',
            eventName: 'click'
        }
    },
    methods: {
        toTitleDate(date) {
            return 'title is : ' + date
        },
        formatDate(date) {
            return Date.parse(date)
        },
        doSomething() {
            console.log('dosonme')
        },
        onSubmit() {
            console.log('submit')
        }
    },
}

</script>



<template>

    <h1>模板语法</h1>

    <hr>
    <h3>文本插值</h3>
    <span>Message: {{ msg }}</span>
    
    <hr>
    <h3>原始 HTML</h3>
    <p>Using text interpolation: {{ rawHtml }}</p>
    <p>Using v-html directive: <span v-html="rawHtml"></span></p>

    <hr>
    <h3>Attribute 绑定</h3>
    <div v-bind:id="dynamicId"></div>
    <div :id="dynamicId"></div>

    <button :disabled="isButtonDisabled">Button</button>

    <div v-bind="objectOfAttrs"></div>

    <hr>
    <h3>使用 JavaScript 表达式</h3>
    {{ number + 1 }}

    {{ ok ? 'YES' : 'NO' }}

    {{ message.split('').reverse().join('') }}

    <div :id="`list-${id}`"></div>

    <time :title="toTitleDate(date)" :datetime="date">
        {{ formatDate(date) }}
    </time>
    

    <hr>
    <h3>指令 Directives</h3>
    <p v-if="seen">Now you see me</p>

    <a v-bind:href="url"> ... </a>
    <a :href="url"> ... </a>

    <a v-on:click="doSomething"> ... </a>
    <a @click="doSomething"> ... </a>

    <a v-bind:[attributeName]="url"> ... </a>
    <a :[attributeName]="url"> ... </a>

    <a v-on:[eventName]="doSomething"> ... </a>
    <a @[eventName]="doSomething"> ... </a>


    <form @submit.prevent="onSubmit">...</form>

</template>