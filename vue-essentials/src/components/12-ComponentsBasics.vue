<script>
import ButtonCounter from './ButtonCounter.vue'
import BlogPost from './BlogPost.vue'
import AlertBox from './AlertBox.vue'

export default {
    components: {
        ButtonCounter,
        BlogPost,
        AlertBox
    },
    data() {
        return {
            count: 0,
            posts: [
                { id: 1, title: 'My journey with Vue' },
                { id: 2, title: 'Blogging with Vue' },
                { id: 3, title: 'Why Vue is so fun' }
            ],
            postFontSize: 1,
            currentTab: 'AlertBox',
            tabs: ['ButtonCounter', 'BlogPost', 'AlertBox']
        }
    }
}
</script>




<template>

    <h1>组件基础</h1>

    <hr>
    <h3>定义一个组件</h3>
    <button @click="count++">You clicked me {{ count }} times.</button>




    <hr>
    <h3>使用组件</h3>
    <h1>Here are many child components!</h1>
	<ButtonCounter />
	<ButtonCounter />
	<ButtonCounter />


    <hr>
    <h3>传递 props</h3>
    <BlogPost
  	    v-for="post in posts"
	    :key="post.id"
  	    :title="post.title"
	></BlogPost>


    <hr>
    <h3>监听事件</h3>
    <div :style="{ fontSize: postFontSize + 'em' }">
    <BlogPost
        v-for="post in posts"
        :key="post.id"
        :title="post.title"
        @enlarge-text="postFontSize += 0.1"
    />
    </div>



    <hr>
    <h3>通过插槽来分配内容</h3>
    <AlertBox>
  	    Something bad happened.
	</AlertBox>



    <hr>
    <h3>动态组件</h3>
    <div class="demo">
        <button
        v-for="tab in tabs"
        :key="tab"
        :class="['tab-button', { active: currentTab === tab }]"
        @click="currentTab = tab"
        >
        {{ tab }}
        </button>
	    <component :is="currentTab" class="tab"></component>
    </div>




    <hr>
    <h3>DOM 内模板解析注意事项</h3>
    


</template>


<style>
.demo {
  font-family: sans-serif;
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
}

.tab-button {
  padding: 6px 10px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: -1px;
  margin-right: -1px;
}
.tab-button:hover {
  background: #e0e0e0;
}
.tab-button.active {
  background: #e0e0e0;
}
.tab {
  border: 1px solid #ccc;
  padding: 10px;
}
</style>