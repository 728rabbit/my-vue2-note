<div>{{ your_target_here }}</div>


var vm = new Vue({
	el: your_element_id,
	data: {
		your_name_here: your_value_here
		....
	},
	methods: {
		your_function_name_here: function() {
			return;
		}
	}
});


1. 使用 v-html 指令用于输出 html 代码


2. v-bind:your_define_name="{your_define_value: binding_conditional_value}"

e.g.
<input type="checkbox" v-model="use" id="r1">
<div v-bind:class="{'class1': use}">
    v-bind:class 指令
</div>


3. v-if="binding_conditional_value"  or v-show="binding_conditional_value" :  Determine whether the element is displayed


4. v-on:click="doSomething": 監聽事件


5. v-model 指令用来在 input、select、textarea、checkbox、radio 等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值。


6. {{ message | capitalize }} 过滤器函数接受表达式的值作为第一个参数。

   过滤器是 JavaScript 函数，因此可以接受参数： {{ message | filterA('arg1', arg2) }}
   
   
7. 缩写  v-bind:href => :href  AND  v-on:click =>  @click


8. 循环语句 v-for 

    <li v-for="site in sites">
      {{ site.name }}
    </li>
	
	<li v-for="(value, key, index) in object">
     {{ index }}. {{ key }} : {{ value }}
    </li>
	
9. 模板 <template>
