选择题
1、下面关于虚拟 DOM 的说法正确的是： ABD
A. 使用虚拟 DOM 不需要手动操作 DOM，可以极大的提高程序的性能。

B. 使用虚拟 DOM 不需要手动操作 DOM，可以极大的提高开发效率。

C. 虚拟 DOM 可以维护程序的状态，通过对比两次状态的差异更新真实 DOM。

D. 虚拟 DOM 本质上是 JavaScript 对象，可以跨平台，例如服务器渲染、Weex 开发等。

2、下面关于 Snabbdom 库的描述错误的是： ABD
A. Snabbdom 库是一个高效的虚拟 DOM 库，Vue.js 的虚拟 DOM 借鉴了 Snabbdom 库。

B. 使用 h() 函数创建 VNode 对象，描述真实 DOM 结构。

C. Snabbdom 库本身可以处理 DOM 的属性、事件、样式等操作。

D. 使用 patch(oldVnode, null) 可以清空页面元素

简答题
1、请简述 patchVnode 函数的执行过程。

1. 触发用户prepatch钩子函数
2. 触发模块update钩子函数、触发用户update钩子函数
3. 如果新节点有text属性，并且text属性和旧节点text属性不同，则需要更新text属性
   1. 此时：如果老节点有children属性，则需要移除老节点的
   2. 如果老节点没有children属性，直接设置新节点的textContent属性
4. 新老节点中是否有children属性，并且两个children属性不相等的时候
   1. 调用`updateChildren`，对比子节点，更新子节点差异
5. 如果只有新节点有children属性并且
   1. 如果老节点有text属性，则清空老节点对应textContent
   2. 如果老节点没有内容，则添加新节点的所有children
6. 如果只有老节点有children属性，新节点没有children属性，则移除老节点的所有children
7. 如果只有老节点有text属性，则清空对应DOM元素的textContent
8. 触发postpatch钩子函数
