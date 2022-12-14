

#### 1. html文本换行问题
```javascript
// 1. 问题描述
文本形式中带有\n换行符时不可以换行

// 2. 问题解决
在对应的元素中添加css样式：
{
  white-space: 'pre-wrap'
}
```

#### 2. useEffect中，指定空数组导致ipcRender监听函数无法获取最新的state问题

```javascript
// 1. 问题分析
useEffect中指定空数组，只在第一次渲染的时候执行监听函数，
此时获取到的将是当前的state，当state更新时，该监听函数不执行，
使用的还是上次的数据。

// 2. 解决问题
a. 使用useRef，在state更新的时候赋值个useRef，
要在监听函数中获取最新值，可获取useRef的current值。

b. 使用setState 回调函数的模式进行设置值
```

<br/>

#### 3. 在使用useReducer的时候，dispatch中传入payload改变state的时候，对于引用类型数据传入state，改变不生效

```javascript
// 1. 问题分析
由于复杂类型的数据在复制改变的时候，原地址是不变的，
而useReducer在dispatch是使用Object.is()方法对state进行比较的
如果地址相同，将不会触发更新state，进而无法出发useEffect监听。

// 2. 解决问题
在dispatch的时候可以使用解构形式改变state
```

#### 4. 在通过ref更新元素滚动的时候，无法直接设置产生预期效果
```js
// 1. 问题分析
当元素的子元素是可控状态下的改变时候，会重新渲染，导致设置的滚动距离错误。
state改变 -> scrollBy设置滚动条滚动 -> 组件重新渲染 -> 滚动条滚动中 -> 组件渲染完成 -> 中断滚动条滚动

// 2. 解决方案
a. 在执行scrollBy的时候加上定时器
b. 在useEffect中执行
```
