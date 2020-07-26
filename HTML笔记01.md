# HTML

注释标签:ctrl +/



## <·head> 中相关标签

### meta标签

- 常用mate标签

  - http-equiv:向浏览器显示正确的信息

    对应属性：“ content”

  - charset：字符编码“ UTF-8” --国际通用 --一个中文字节3bytes   “ gb2312”中国字库---2bytes---

  - name：便于搜索引擎检索，关键字可以用；隔开

    ​				对应属性content：其中内容用户搜索引擎查找关键字



## <·body>中相关标签

### 1.1 排版标签

​	1) 标题标签hx

​	2) 段落标签p

​	3) 换行标签 br

​	4) 水平划线标签 hr

​	5) div和span标签

- 可以附加很多属性

  - ```
    <div id='...'>...</div> 一行只能放一个
    ```

  - ```
    <span>..</span>一行放好几个标签
    ```

     

### 1.2  文本格式化标签

|            |  粗体  | 斜体 | 加删除线 | 下划线 | 推荐使用   |
| ---------- | :----: | ---- | -------- | ------ | ---------- |
| 强调语气   | strong | em   | del      | ins    | XHTML      |
| 单纯的样式 |  <b>   | <i>  | <s>      | <u>    | 一般不推荐 |

### 1.3  图像标签img

```
<img src="图片地址”  alt=“下载失败时的替换文本” title='提示文本'>
```

- **src**：指定文件路径
  - 相对路径：对于当前文件下的路径
    - 上级目录：../xxfile/img.jpg
    - 同级目录：img.jpg

- alt:  图裂时展示，或者协助盲人听图

- title：鼠标放图片上展示

- border:设置图像边框的宽度

- width:设置图像的宽度 witdth="100"  <!--像素-->

- height:设置图像高度 height="300"

  <!--以上标签的属性-->



### 1.4 链接标签 a

#### 1) href

```
<a href='目标地址' title='鼠标滑过显示的文本'>链接显示的文本</a>
```

- `href`=‘ ....’：链接指向的页面地址

  - 外部链接

    - http://www.baidu.com     <!-- http:// -->  

  - 内部链接

    - ```
      <a href="day01/global.html">
      ```

    - 相对路径：相对于当前文件的路径       <!-- 起始是网页地址-->

    ​		http://127.0.0.1:5500/day01/global.html

  - 空链接

    - ```
      <a href="#">...</a> #有时候链接没做好用#代替
      ```

- `target`="..." :目标窗口弹出方式，默认是在当前窗口跳转

  - target='_blank'      //blank:空白页
  - target='_self'    //默认属性

- 默认样式丑！

  - 文字颜色为蓝色，点击后为紫色，可以通过css改变

#### 2)跳转到顶部

```
<div name="top"></div>   	//1.在顶部设置空标签，name属									//	性值相当于一个锚的名字
...正文					   //2.正文长度大于浏览器高度就会出							 	//   现进度条
<a href="#top">点我回顶部</a> //3.跳转到锚名为top的指定位置
```

#### 3)邮件

```
<a href="mailto:xxxx@qq.com">email to xxx</a>
```



<hr>

6. ul-li && ol-li列表标签
   - ul   > ul-li:无序列表
     - vsco 快捷方式 ul>li*n 快速创建多个无序标签
     - ul-li的默认样式前面有多个原点
   - ol   >ol-li:有序列表
     - 自带序号

<hr>

8. 表格

- table

- tr:行

- td:单元格，一行中有几个人单元格就有几列

- th：表格头部的一个单元格

  <table>
      <tr>
          <th>表格元素</th>
          <th>元素功能</th>
      </tr>
      <tr>
          <td>
              tr
          </td>
          <td>
              行
          </td>
      </tr>
      <tr>
          <td>
              td
          </td>
    		<td>
              每行中的单元格，几个单元格单标有几列
          </td>
      </tr>
      <tr>
          <td>
              th
          </td>
          <td>
              表头单元格
          </td>
      </tr>
  </table>

  在浏览器总是还没有表格线这些样式的，需要css 添加样式

  表头th默认是粗体+居中

9. 给<table>添加border 属性，为表格添加边框

table表格在没有添加css 之前是没有边框的，我们可以给table 添加border属性，并且设置该值为1

```
<tabel border ='1'>...</table>
```

<img src="E:\HTML\day01\md笔记\tableBorder.png" alt="1581321668105" style="zoom:100%;" />

​		很细的表格线

```
<tabel cellspacing='0' border='1'>...</table>
```

![1581322003661](E:\HTML\day01\md笔记\tableCellspacingBorder.png)

10. caption标签，为表格添加标题

```
<caption>表格标题</caption>
```

​	显示位置：表格的上方

11.单元格合并：colspan && rowspan

- 横向合并

  ```
  <th colspan='2'>
  ```

  必须指出合并的列数目，是两列还是三列

- 纵向合并

  ```
  td rowspan="2"
  ```

  必须指出合并的行数目，是几行

  注意：一行里面新增一列后，其他行也会在行末补充新的列

  rowspan="3"：th+2td

  ![1581322973687](E:\HTML\day01\md笔记\rowspan.png)

<hr>


<hr>

## <·form>表单

表单：可以将浏览器输入的数据发送给服务端，服务器就可以处理表单传过来的数据。

1. 数据传送地址&&传送方式

```
<form method="传送方式" action="服务器文件">....</form>
```

- action:数据传送目标地址

- method:数据传送方式（get/post）

2. 文本输入框，密码输入框

```
<form action=".." method="get">
    <!--w文本输入框-->
    <input type="text" name="名称" value="文本" placeholder='请输入用户名'/>
    <!--密码输入框-->
    <input type="passwd" name="名称" value="密码" placeholder='请输入密码'/>
</form>
```



- type:

  - type="text",文本输入框
  - type="passwd",密码输入框
  - type="radio":圆形选择框
  - type="checkbox"：方形选择框

- name:

  - 文本输入框，用于给后台java/php 使用

  - 同一组的单选按钮，需要name值一致，才能起到单选的作用

- value:

  给文本输入框设置默认值，一般提到提示作用

- checked="checked" 表示被选中

- placeholder:提示用户内容的输入格式

  

  

3. 下拉列表

   