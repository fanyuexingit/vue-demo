<script>
export default {
  data() {
    return {
      count: 1,
      someObject: {},
      obj: {
        nested: { count: 0 },
        arr: ['foo', 'bar']
      }
    }
  },
  methods: {
    increment() {
      this.count++
    },
    // increment: () => {
    //   // 反例：无法访问此处的 `this`!
    // },
    // async increment() {
    //   this.count++
    //   await nextTick()
    //   // 现在 DOM 已经更新了
    // },
    mutateDeeply() {
      this.obj.nested.count++
      this.obj.arr.push('baz')
    }
  },
  mounted() {
    console.log(this.count)
    this.count = 2

    // 响应式代理 vs. 原始值
    const newObject = {}
    this.someObject = newObject
    console.log(newObject === this.someObject) // false


    // 在其他方法或是生命周期中也可以调用方法
    this.increment()
  }
}
</script>




<template>
    <h1>响应式基础</h1>

    <hr>
    <h3>声明响应式状态</h3>
    Count is: {{ count }}


    <hr>
    <h3>声明方法</h3>
    <button @click="increment">{{ count }}</button>

    <button @click="mutateDeeply"></button>
    <label>{{ obj.nested.count }}</label>
    <label> {{  obj.arr }}</label>


</template>