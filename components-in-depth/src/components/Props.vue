<script>

import BlogPost from './BlogPost.vue';

export default {
    components: { 
        BlogPost 
    },
    data() {
        return {
            count: 0,
            post: { id: 1, title: 'My journey with Vue' },
            posts: [
                { id: 1, title: 'My journey with Vue' },
                { id: 2, title: 'Blogging with Vue' },
                { id: 3, title: 'Why Vue is so fun' }
            ],
            postFontSize: 1,
        }
    }
}

</script>




<template>

    <h1>Props</h1>

    <hr>
    <h3>Props 声明</h3>

    <hr>
    <h3>传递 prop 的细节</h3>



    <h4>Prop 名字格式</h4>
    <!-- 实际上为了和 HTML attribute 对齐，我们通常会将其写为 kebab-case 形式 -->
    <BlogPost greeting-message="hello" />



    <h4>静态 vs. 动态 Prop</h4>
    <!-- 静态 -->
    <BlogPost title="My journey with Vue" />

    <!-- 根据一个变量的值动态传入 -->
    <BlogPost :title="post.title" />

    <!-- 根据一个更复杂表达式的值动态传入 -->
    <BlogPost :title="post.title + ' by ' + post.id" />



    <h4>传递不同的值类型</h4>
    Number
    <!-- 虽然 `42` 是个常量，我们还是需要使用 v-bind -->
    <!-- 因为这是一个 JavaScript 表达式而不是一个字符串 -->
    <!-- <BlogPost :likes="42" /> -->

    <!-- 根据一个变量的值动态传入 -->
    <!-- <BlogPost :likes="post.likes" /> -->

    Boolean
    <!-- 仅写上 prop 但不传值，会隐式转换为 `true` -->
    <!-- <BlogPost is-published /> -->

    <!-- 虽然 `false` 是静态的值，我们还是需要使用 v-bind -->
    <!-- 因为这是一个 JavaScript 表达式而不是一个字符串 -->
    <!-- <BlogPost :is-published="false" /> -->

    <!-- 根据一个变量的值动态传入 -->
    <!-- <BlogPost :is-published="post.isPublished" /> -->

    Array
    <!-- 虽然这个数组是个常量，我们还是需要使用 v-bind -->
    <!-- 因为这是一个 JavaScript 表达式而不是一个字符串 -->
    <!-- <BlogPost :comment-ids="[234, 266, 273]" /> -->

    <!-- 根据一个变量的值动态传入 -->
    <!-- <BlogPost :comment-ids="post.commentIds" /> -->

    Object
    <!-- 虽然这个对象字面量是个常量，我们还是需要使用 v-bind -->
    <!-- 因为这是一个 JavaScript 表达式而不是一个字符串 -->
    <!-- <BlogPost
    :author="{
        name: 'Veronica',
        company: 'Veridian Dynamics'
    }"
    /> -->

    <!-- 根据一个变量的值动态传入 -->
    <!-- <BlogPost :author="post.author" /> -->



    <h4>使用一个对象绑定多个 prop</h4>

    <!-- 等效 -->
    <BlogPost v-bind="post" />
    <BlogPost :id="post.id" :title="post.title" />



    <hr>
    <h3>单向数据流</h3>

    <hr>
    <h3>Prop 校验</h3>
    String
    Number
    Boolean
    Array
    Object
    Date
    Function
    Symbol
    自定义


    <hr>
    <h3>Boolean 类型转换</h3>
</template>