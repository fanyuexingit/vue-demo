<script>

export default {
    data() {
        return {
            message: '',
            checked: true,
            checkedNames: [],
            picked: 'One',
            selected: '',
            selected2: '',
            selected3: 'A',
            options: [
                { text: 'One', value: 'A' },
                { text: 'Two', value: 'B' },
                { text: 'Three', value: 'C' }
            ],
            toggle: 'click it!',
            dynamicTrueValue: 'positive',
            dynamicFalseValue: 'negative',
            pick: "pick",
            value: 'value',
            selectedNum: 'selectedNum',
            msg: 'msg',
            age: 0,
            msg2: 'msg2'
        }
    }
}

</script>



<template>

    <h1>表单输入绑定</h1>

    <hr>
    <h3>基本用法</h3>

    <p>Message is: {{ message }}</p>
    <input v-model="message" placeholder="edit me" />

    <p>Multiline message is: {{ message }}</p>
    <textarea v-model="message" placeholder="add multiple lines"></textarea>

    <p>checkbox: {{ checked }}</p>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label>




    
    <div>Checked names: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
    <label for="jack">Jack</label>

    <input type="checkbox" id="john" value="John" v-model="checkedNames">
    <label for="john">John</label>

    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
    <label for="mike">Mike</label>



    <div>Picked: {{ picked }}</div>

    <input type="radio" id="one" value="One" v-model="picked" />
    <label for="one">One</label>

    <input type="radio" id="two" value="Two" v-model="picked" />
    <label for="two">Two</label>



    <div>Selected: {{ selected }}</div>

    <select v-model="selected">
        <option disabled value="">Please select one</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
    </select>

    <div>Selected: {{ selected2 }}</div>

    <select v-model="selected2" multiple>
        <option>A</option>
        <option>B</option>
        <option>C</option>
    </select>


    <div>Selected: {{ selected3 }}</div>

    <select v-model="selected3">
        <option v-for="option in options" :value="option.value">
            {{ option.text }}
        </option>
    </select>

    


    <hr>
    <h3>值绑定</h3>

    <div>{{ toggle }}</div>
    <!-- toggle 属性的值会在选中时被设为 'yes'，取消选择时设为 'no' -->
    <input
        type="checkbox"
        v-model="toggle"
        true-value="yes"
        false-value="no" />
    <!-- 可以通过 v-bind 将其绑定为其他动态值 -->
    <input
        type="checkbox"
        v-model="toggle"
        :true-value="dynamicTrueValue"
        :false-value="dynamicFalseValue" />

    <div>{{ pick }}</div>
    <!-- pick 会在第一个按钮选中时被设为 first，在第二个按钮选中时被设为 second -->??????????????????????????????
    <input type="radio" v-model="pick" :value="first" />
    <input type="radio" v-model="pick" :value="second" />

    <div>{{ selectedNum }}</div>
    <!-- selected 会被设为该对象字面量值 { number: 123 } -->
    <select v-model="selectedNum">
        <option :value="{ number: 123 }">123</option>
    </select>




    <hr>
    <h3>修饰符</h3>

    <!-- 在 "change" 事件后同步更新而不是 "input" -->
    <div>{{ msg }}</div>
    <input v-model.lazy="msg" />

    <div>{{ age }}</div>
    <input v-model.number="age" type="number"/>

    <div>{{ msg2 }}</div>
    <input v-model.trim="msg2" />

</template>