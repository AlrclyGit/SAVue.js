- v-cloak
- v-text
- v-html
- v-model  双向数据绑定，使用于 input 
- v-bind:value="show" => :value
- v-on:click="show" => @click
  - @click.stop =  阻止冒泡
  - @click.capture = 捕获机制
  - @click.prevent = 阻止默认行为
  - @click.self = 不受冒泡、捕获的影响
  - @click.once = 只触发一次



### Class

```
<h1 :class="['red','italic']">这是一个大的H1</h1>
<h1 :class="['red','italic',flag ? 'active' : '']">这是一个大的H1</h1>
<h1 :class="['red','italic',{'active': flag}]">这是一个大的H1</h1>
<h1 :class="{red: true, thin: true, italic: false, active: false}">这是一个大的H1</h1>
<h1 :class="classObj">这是一个大的H1</h1>
```



### Styel

```
<h1 :style="{ 'color':'red','font-weight': 200}">{{msg}}</h1>
<h1 :style="[styleObj2]">{{msg}}</h1>
```



### FOR

```
<p v-for="(val,key,index) in list" :key="item.id">{{key}}_{{val.name}}_{{index}}</p>
<p v-for="count in 10">这是第{{count}}次循环</p>
```



### IF

```
<h3 v-if="flag">v-if</h3> 重新删除或创建元素
<h3 v-show="flag">v-show</h3> 只是切换了 display
```



### 定义私有过滤器、指令

```
var vm2 = new Vue({
    el: '#app2',
    data: {
        dt: new Date()
    },
    methods: {},
    filters: { // 定义私有过滤器
        dateFormat: function (dataStr, pattern = '') {
            var dt = new Date(dataStr);
            var y = dt.getFullYear().toString().padStart(4, "0");
            var m = (dt.getMonth() + 1).toString().padStart(2, "0");
            var d = dt.getDate().toString().padStart(2, "0");
            return `${y}-${m}-${d}`
        }
    },
    directives: { //定义私有指令
        'fontWeight': {
            bind: function (el, binding) {
                el.style.fontWeight = binding.value
            }
        },
        'fontSize': function (el,binding){ // 方法定义的简写形式
            el.style.fontSize = parseInt(binding.value) + 'px'
        }
    }
})
```

