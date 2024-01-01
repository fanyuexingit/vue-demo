<script>
import ButtonCounter from './ButtonCounter.vue'

export default {
  components: {
    ButtonCounter
  }
}



</script>



<template>

    <h1>组件注册</h1>

    <hr>
    <h3>全局注册</h3>

    <p>
        import MyComponent from './App.vue'
<br>
        app.component('MyComponent', MyComponent)
    </p>



    <hr>
    <h3>局部注册</h3>

    <ButtonCounter/>



    <hr>
    <h3>组件名格式</h3>

    <p>PascalCase </p>
    <p>kebab-case</p>

</template>
