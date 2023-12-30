<script>

export default {
    data() {
        return {
            parentMessage: 'Parent',
            items: [{ message: 'Foo' }, { message: 'Bar' }],
            myObject: {
                title: 'How to do lists in Vue',
                author: 'Jane Doe',
                publishedAt: '2016-04-10'
            },
            todos: [
                {
                    id: 1,
                    name: 'fan',
                    text: 'qwer'
                },
                {
                    id: 2,
                    name: 'yue',
                    text: 'asdf'   
                },
                {
                    id: 3,
                    name: 'xin',
                    text: 'zcxv'   
                }
            ],
            numbers: [1, 2, 3, 4, 5],
            sets: [[ 1, 2, 3, 4, 5 ], [6, 7, 8, 9, 10]]
        }
    },
    methods: {
        even(numbers) {
            return numbers.filter(number => number % 2 === 0)
        }
    },
    computed: {
        evenNumbers() {
            return this.numbers.filter(n => n % 2 === 0)
        }
    }
}
</script>



<template>

    <h1>列表渲染</h1>

    <hr>
    <h3>v-for</h3>

    111
    <li v-for="item in items">
        {{ item.message }}
    </li>
    <li v-for="(item, index) in items">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
    </li>

    222
    <li v-for="{ message } in items">
    {{ message }}
    </li>
    <li v-for="({ message }, index) in items">
    {{ message }} {{ index }}
    </li>

    333
    <div v-for="item of items">
        {{ item.message }}
    </div>

    for  for
    <li v-for="item in items">
    <span v-for="childItem in item.children">
        {{ item.message }} {{ childItem }}
    </span>
    </li>


    <hr>
    <h3>v-for 与对象</h3>

    <ul>
        <li v-for="value in myObject">
            {{ value }}
        </li>
    </ul>

    <ul>
        <li v-for="(value, key) in myObject">
            {{ key }}: {{ value }}
        </li>
    </ul>
    

    <ul>
        <li v-for="(value, key, index) in myObject">
            {{ index }}. {{ key }}: {{ value }}
        </li>
    </ul>


    <hr>
    <h3>v-for 其他</h3>
    <span v-for="n in 10">{{ n }}</span>

    <ul>
    <template v-for="item in items">
        <li>{{ item.message }}</li>
        <li class="divider" role="presentation"></li>
    </template>
    </ul>



    <hr>
    <h3>通过 key 管理状态</h3>
    
    <div v-for="todo in todos" :key="todo.id">
        <li>{{ todo }}</li>
    </div>

    <template v-for="todo in todos" :key="todo.name">
        <li>{{ todo.text }}</li>
    </template>


    <hr>
    <h3>组件上使用 v-for</h3>
    <MyComponent v-for="item in items" :key="item.id" />
    <MyComponent
        v-for="(item, index) in items"
        :item="item"
        :index="index"
        :key="item.id"
    />


    <hr>
    <h3>数组变化侦测</h3>
    变更方法
    push()
    pop()
    shift()
    unshift()
    splice()
    sort()
    reverse()
    非变更方法
    filter()
    concat()
    slice()
    ...
    this.items = this.items.filter((item) => item.message.match(/Foo/))


    <hr>
    <h3>展示过滤或排序后的结果</h3>

    <li v-for="n in evenNumbers">{{ n }}</li>


    <ul v-for="numbers in sets">
        <li v-for="n in even(numbers)">{{ n }}</li>
    </ul>

</template>