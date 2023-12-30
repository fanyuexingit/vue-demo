<script>
export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      },
      firstName: 'John',
      lastName: 'Doe'
    }
  },
  methods: {
    calculateBooksMessage() {
        return this.author.books.length > 0 ? 'Yes' : 'No'
    },
    testName(name) {
        return this.fullName = name
    }
  },
  computed: {
    // 一个计算属性的 getter
    // 计算属性值会基于其响应式依赖被缓存
    // 无论多少次访问 publishedBooksMessage 都会立即返回先前的计算结果，而不用重复执行 getter 函数
    publishedBooksMessage() {
      return this.author.books.length > 0 ? 'Yes' : 'No'
    },
    // 计算属性永远不会更新，因为 Date.now() 并不是一个响应式依赖
    now() {
        return Date.now()
    },
    // 计算属性默认是只读的
    // 用到“可写”的属性，你可以通过同时提供 getter 和 setter 来创建
    fullName: {
      // getter
      get() {
        return this.firstName + ' ' + this.lastName
      },
      // setter
      set(newValue) {
        // 注意：我们这里使用的是解构赋值语法
        [this.firstName, this.lastName] = newValue.split(' ')
      }
    }
    
  }
}
</script>




<template>
    <h1>计算属性</h1>

    <hr>
    <h3>基础示例</h3>
    <p>Has published books:</p>
    <span>{{ publishedBooksMessage }}</span>


    <hr>
    <h3>计算属性缓存 vs 方法</h3>
    <p>{{ calculateBooksMessage() }}</p>

    <p>{{ now }}</p>


    <hr>
    <h3>可写计算属性</h3>
    <button @click="testName('fan yuexin')"></button>
    <span>{{ firstName }}</span>
    <span>{{ lastName }}</span>

    
</template>