<script>


class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName
    this.lastName = lastName
  }
}



export default {
  props: ['title'],
  // 字符串数组来声明
  props: ['foo'],
  // 对象的形式来声明
  props: {
    title: String,
    likes: Number,
    // 如果一个 prop 的名字很长，应使用 camelCase 形式
    greetingMessage: String
  },




  props: {
    author: Person
  },
  props: {
    // 基础类型检查
    //（给出 `null` 和 `undefined` 值则会跳过任何类型检查）
    propA: Number,
    // 多种可能的类型
    propB: [String, Number],
    // 必传，且为 String 类型
    propC: {
      type: String,
      required: true
    },
    // Number 类型的默认值
    propD: {
      type: Number,
      default: 100
    },
    // 对象类型的默认值
    propE: {
      type: Object,
      // 对象或者数组应当用工厂函数返回。
      // 工厂函数会收到组件所接收的原始 props
      // 作为参数
      default(rawProps) {
        return { message: 'hello' }
      }
    },
    // 自定义类型校验函数
    propF: {
      validator(value) {
        // The value must match one of these strings
        return ['success', 'warning', 'danger'].includes(value)
      }
    },
    // 函数类型的默认值
    propG: {
      type: Function,
      // 不像对象或数组的默认，这不是一个
      // 工厂函数。这会是一个用来作为默认值的函数
      default() {
        return 'Default function'
      }
    }
  },



  created() {
    // props 会暴露到 `this` 上
    console.log(this.foo)
  }
}
</script>

<template>
  <span>{{ greetingMessage }}</span>
  <h4>{{ title }}</h4>
  <button @click="$emit('enlarge-text')">Enlarge text</button>
</template>