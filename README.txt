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


01. 使用 v-html 指令用于输出 html 代码


02. v-bind:your_define_name="{your_define_value: binding_conditional_value}"

	e.g.
	<input type="checkbox" v-model="use" id="r1">
	<div v-bind:class="{'class1': use}">
		v-bind:class 指令
	</div>


03. v-if="binding_conditional_value"  or v-show="binding_conditional_value" :  Determine whether the element is displayed


04. v-on:click="doSomething": 監聽事件


05. v-model 指令用来在 input、select、textarea、checkbox、radio 等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值。


06. {{ message | capitalize }} 过滤器函数接受表达式的值作为第一个参数。

    过滤器是 JavaScript 函数，因此可以接受参数： {{ message | filterA('arg1', arg2) }}
   
   
07. 缩写  v-bind:href => :href  AND  v-on:click =>  @click


08. 循环语句 v-for 

    <li v-for="site in sites">
      {{ site.name }}
    </li>
	
	<li v-for="(value, key, index) in object">
     {{ index }}. {{ key }} : {{ value }}
    </li>
	
09. 模板 <template>


10. computed vs methods
	我们可以使用 methods 来替代 computed，效果上两个都是一样的，但是 computed 是基于它的依赖缓存，
	只有相关依赖发生改变时才会重新取值。而使用 methods ，在重新渲染的时候，函数总会重新调用执行。
	
	可以说使用 computed 性能会更好，但是如果你不希望缓存，你可以使用 methods 属性。
	
	computed: {
		// 计算属性的 getter
		reversedMessage: function () {
		  // `this` 指向 vm 实例
		  return this.message.split('').reverse().join('')
		}
    }
	
	methods: {
		reversedMessage2: function () {
			return this.message.split('').reverse().join('')
		}
	}
	
	
	computed 属性默认只有 getter ，不过在需要时你也可以提供一个 setter
	
	computed: {
		site: {
		  // getter
		  get: function () {
			return this.name + ' ' + this.url
		  },
		  // setter
		  set: function (newValue) {
			var names = newValue.split(' ')
			this.name = names[0]
			this.url = names[names.length - 1]
	    }
    }
	
11. 监听属性 watch: 通过 watch 来响应数据的变化

	<button @click = "counter++" style = "font-size:25px;">点我</button>
	
	vm.$watch('counter', function(nval, oval) {
		alert('计数器值的变化 :' + oval + ' 变为 ' + nval + '!');
	});


12. v-bind:class="{ 'active': isActive, 'text-danger': hasError }"
	new Vue({
	  el: '#app',
	  data: {
		isActive: true,
		hasError: true
	  }
	});
	
13. <input v-on:keyup.enter="submit">


14. 表单
    <div id="app">
	  <p>input 元素：</p>
	  <input v-model="message" placeholder="编辑我……">
	  <p>消息是: {{ message }}</p>
		
	  <p>textarea 元素：</p>
	  <p style="white-space: pre">{{ message2 }}</p>
	  <textarea v-model="message2" placeholder="多行文本输入……"></textarea>
	</div>
	 
	<script>
	new Vue({
	  el: '#app',
	  data: {
		message: 'Runoob',
		message2: 'xxxxxxxx'
	  }
	})
	</script>
	
	<input type="checkbox" id="checkbox" v-model="checked">
	
	<input type="radio" id="runoob" value="Runoob" v-model="picked">
	
	<select v-model="selected" name="fruit">
	
	
	<input v-model.lazy="msg" >
    在默认情况下， v-model 在 input 事件中同步输入框的值与数据，但你可以添加一个修饰符 lazy ，
	从而转变为在 change 事件中同步
	 
	<input v-model.number="age" type="number">
	如果想自动将用户的输入值转为 Number 类型（如果原值的转换结果为 NaN 则返回原值），
	可以添加一个修饰符 number 给 v-model 来处理输入值
	
	<input v-model.trim="msg">
	如果要自动过滤用户输入的首尾空格，可以添加 trim 修饰符到 v-model 上过滤输入
	
15. 组件 Vue.component(tagName, options)

    <div id="app">
		<runoob></runoob>
	</div>

	<script>
	// 注册
	Vue.component('runoob', {
	  template: '<h1>自定义组件!</h1>'
	})
	// 创建根实例
	new Vue({
	  el: '#app'
	})
	</script>
	
	或
	
	<div id="app">
		<runoob></runoob>
	</div>
	 
	<script>
	var Child = {
	  template: '<h1>自定义组件!</h1>'
	}
	 
	// 创建根实例
	new Vue({
	  el: '#app',
	  components: {
		// <runoob> 将只在父模板可用
		'runoob': Child
	  }
	})
	</script>
	
	
	
	prop 是子组件用来接受父组件传递过来的数据的一个自定义属性。

    父组件的数据需要通过 props 把数据传给子组件，子组件需要显式地用 props 选项声明 "prop"：
	
	<div id="app">
		<child message="hello!"></child>
	</div>
	 
	<script>
	// 注册
	Vue.component('child', {
	  // 声明 props
	  props: ['message'],
	  // 同样也可以在 vm 实例中像 "this.message" 这样使用
	  template: '<span>{{ message }}</span>'
	})
	// 创建根实例
	new Vue({
	  el: '#app'
	})
	</script>
	
16. Ajax(axios)
    
	axios.get('/user', {
		params: {
		  ID: 12345
		}
	  })
	  .then(function (response) {
		console.log(response);
	  })
	  .catch(function (error) {
		console.log(error);
	  });
	
	
	执行多个并发请求
	function getUserAccount() {
	  return axios.get('/user/12345');
	}
	 
	function getUserPermissions() {
	  return axios.get('/user/12345/permissions');
	}
	axios.all([getUserAccount(), getUserPermissions()])
	  .then(axios.spread(function (acct, perms) {
		// 两个请求现在都执行完成
	  }));
