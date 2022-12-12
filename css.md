#### flex: 1;的情况下设置overflow不生效

```javascript
// 1. 解决方法
flex:1的元素的父元素必须保证高度或者宽度有具体的数值；
如果父元素的高度或者宽度也是flex:1自适应的，
最好在父元素上也设置overflow:auto，这样子元素的overflow:auto生效了；（BFC妙用
```

#### 文字超出显示省略号

```less
c// 文字超出显示省略, 父元素要设置overflow: hidden
.father {
  overflow: hidden;
}

.omit {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

#### electron 中无边框拖拽

```less
.bar {  // 需要进行拖拽的盒子
  -webkit-app-region: drag; // 设置
  -webkit-user-select: none; 
  user-select: none;
}
// 子盒子中需要设置no-drag才可点击
.child {
  -webkit-app-region: no-drag;
}
```

#### css中设置渐变背景

```less
.bar {
  // background-image: linear-gradient( 角度/deg , 颜色);
  background-image: linear-gradient(to right , #7A88FF, #7AFFAF);
}
```

#### css中设置渐变边框

```less
.bar {
  border: 1px solid;
  border-image: linear-gradient(to right, #fff, #ccc);
}
```

#### css鼠标拖拽样式

```less
.bar {
  cursor: move;
}
```


#### css画三角形

```less
.bar {
  &::before {
  	left: -20px;
  	position: absolute;
  	content: '';
  	border: 6px solid #7c7ce1;
  	border-left-color: transparent;
  	border-top-color: transparent;
  	transform: rotate(-45deg);
  }
}
```

#### css去除input默认样式

```less
.bar {
  background: none;  
	outline: none;  
	border: 0px;
	text-indent: 1rem; // 首行缩进
}
```

#### css flex布局下文字超出换行

```less
.bar {
  display: flex;
  max-width: 200px;
	word-break: break-all;
}
```


#### flex 布局下子元素的宽度被压缩
```less
// flex-shrink 属性指定了 flex 元素的收缩规则。flex 元素仅在默认宽度之和大于容器的时候才会发生收缩，其收缩的大小是依据 flex-shrink 的值

// 在子元素中添加  
flex-shrink:0;
```