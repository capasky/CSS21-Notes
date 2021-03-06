# CSS 2.1 规范 阅读摘要及笔记
---
# 目录

1. 关于CSS 2.1 规范
2. CSS 2.1 简介
3. 规范的一致性：要求和建议
4. 语法和基本数据类型
5. 选择器
6. 指配的属性值、层叠和继承
7. 媒体类型
8. 盒（框）模型
9. 视觉格式化模型
10. [视觉格式化模型细节](#视觉格式化模型细节)
11. 可视效果
12. [内容生成、自动编号及列表](#内容生成、自动编号及列表)
13. 分页媒体
14. 颜色和背景
15. 字体
16. [文本](#文本)
17. 表格
18. 用户接口
* Appendix A. Aural style sheets
* Appendix B. Bibliography
* Appendix C. Changes
* Appendix D. 用于HTML 4的默认样式表
* Appendix E. Elaborate description of Stacking Contexts
* Appendix F. Full property table
* Appendix G. Grammar of CSS 2.1
* Appendix I. Index

这个repo仅为个人阅读笔记。谢谢。
__1-3章为介绍，略__
#语法和基本数据类型
---
##语法
总结几个注意点：

1. 所有CSS语法是大小写不敏感的
2. @规则：@后跟标识符，然后是 **;** 或一个 **块**

##数据类型

#视觉格式化模型细节
---
##包含块
元素框的位置和大小通常会相对于某个特定的矩形来计算，这个矩形称作元素的 **包含块**。一个包含块的定义如下：

1. 根元素的包含块是被称作 **初始包含块** 的矩形。对于连续媒体（如浏览器）来说，就是 **视口**。
2. 对于其他元素，如果这个元素的位置属性为 `relative` 或 `static`，包含块由最近的快容器祖先元素的 **内容边界** 形成。
3. 如果元素是固定定位： `position: fixed;`，其包含块由视口形成。
4. 如果元素是绝对定位： `position: absolute;`，其包含块由最近的定位祖先元素通过以下方式形成：
	1. 若祖先元素是行内元素时，包含块为绕着为该元素生成的第一个和最后一个行内框（inline boxes）的填充框（padding boxes）的边界。在CSS2.1  中，如果一个行内元素被分割成多行，其包含块是未定义的。
	2. 否则，包含块由祖先元素的 **填充边缘（padding edge）** 形成。

	若没有这样的祖先元素，则包含块为初始包含块。

确定了包含块，即可确定在盒模型中如何计算元素的位置。如绝对定位的元素。
## 内容宽度： `width` 属性

# 内容生成、自动编号及列表
---
CSS2.1中，内容可以由两种方式生成：
* ‘content’属性以及与之关联的:before和:after伪元素
* ‘display’属性设置为‘list-item’的元素

## befor和after伪元素
元素的文档树 **内容** 之前或之后


# 16.文本
---
## 空白处理：‘white-space’属性
这个属性定义了元素内的空白如何处理，它有以下的值：

* normal 合并连续的空白字符。填充行框时，若有必要（行满），则会换行。
* pre 不合并连续的空白字符，文档中存在多少 **空白字符** 就显示几个 **空白字符** 。换行仅在遇到显式的换行符（**\n**）时发生。这个属性完全还原了文档中的内容。
* nowrap 和 normal 一样会合并空白字符，但 **死都不换行**。
* pre-wrap 同 pre，只是在填充行框时，若有必要，也会换行。
* pre-line 合并连续的空白字符，换行机制同pre-wrap，即遇到换行符或需要时换行。 

其中，**空白字符** 包含空格、tab
源文件中的新行可由回车（U+000D)、换行（U+000A)或同时（0d0a）表示。  
通常的浏览器会有以下默认值：  
```css
	pre { white-space: pre; }
	p { white-space: normal; }
```

# 18.用户接口
---
## 'cursor'属性
该属性指定光标样式，值可以为：

* uri
* auto|default|pointer...
* inherit

## 'outline'属性
outline与border的区别：

1. outline不占用空间，即不参与盒模型计算
2. outline不一定是矩形

