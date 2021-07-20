# TinUI

## 项目类型

TinUI是一个基于tkinter（Python/tcl/tk）的拓展组件（Widget），可以绘制虚拟组件。

TinUI基于tkinter的画布（Canvas），可以作为整个窗口的唯一控件。TinUI能够通过自身绘制出功能组件和文字，也可以使用画布功能添加组件。使用TinUI，可以使界面设计和代码设计分离，此外，TinUI绘制的虚拟组件速度更快，样式更加丰富。

目前，TinUI还处于完善阶段。

## 依赖

目前，TinUI没有依赖项目。

## TinEngine支持

[TinEngine](https://blog.csdn.net/tinga_kilin/category_10332845.html)使用了TinUI。

---

## 创建TinUI

```python
tinui=TinUI(root,bg='white',update=True,update_time=1000)
'''
update:bool::是否实时更新滚动画面
update_time:int::每次更新滚动画面的间隔（毫秒）
**kw::Canvas的参数
'''
```



---

## 基础函数

> ==一般地==，会将每个函数的名称以及定义、参数内容、函数绘制说明列出来。
>
> 所有函数均会返回主要画布对象。

### add_title(self,pos:tuple,text:str,fg='black',font='微软雅黑',size=1,anchor='nw',**kw)

- pos::位置
- text::标题文字
- fg::文本颜色
- font::文本字体
- size::文本字体大小。依据字典：`{0:20,1:18,2:16,3:14,4:12}`
- anchor::对齐方向

绘制一个大字体标题。

### return: title

---

### add_paragraph(self,pos:tuple,text:str,fg='black',font=('微软雅黑',12),side='left',width=500,anchor='nw',**kw)

- pos::位置
- text::标题文字
- fg::文本颜色
- font::字体名称+大小
- side::对齐方向
- width::一行允许的最大字符宽度
- anchor::对齐方向

绘制一个段落。

### return: paragraph

---

### add_button(self,pos:tuple,text:str,fg='black',bg='#E1E1E1',activefg='black',activebg='#E5F1FB',font=('微软雅黑',12),command=None,anchor='nw')

- pos::位置
- text::标题文字
- fg::文字颜色
- bg::按钮颜色
- activefg::相应鼠标的文本颜色
- activebg::相应鼠标的按钮颜色
- font::字体名称+大小
- command::绑定的函数。该函数**必须要有event参数**，因为TinUI的按钮会传递点击事件的event
- anchor::对齐方向

绘制一个按钮。这个按钮会响应鼠标的离开和进入事件，被单击时也会调用绑定的函数。

### return: button_text, button_back

---

### add_label(self,pos:tuple,text:str,fg='black',bg='#f0f0f0',outline='grey',font=('微软雅黑',12),anchor='nw') 

- pos::位置
- text::标题文字
- fg::文字颜色
- bg::背景色
- outline::边框颜色
- font::字体名称+大小
- anchor::对齐方向

绘制一个类Label组件。

### return: label

---

### add_checkbutton(self,pos:tuple,text:str,fg='black',fill='lightgreen',font=('微软雅黑',12),command=None,anchor='nw')

- pos::位置
- text::标题文字
- fg::文字颜色
- fill::选中的标识填充
- font::字体名称+大小
- command::绑定的函数。该函数**必须要有event参数**，因为TinUI的按钮会传递点击事件的event
- anchor::对齐方向

绘制一个复选框。这个复选框会响应鼠标的离开和进入事件，被单击时也会调用绑定的函数，并且会根据当前样式更改点击后的样式。

### return: check_text, check_mark

---

### add_entry(self,pos:tuple,width:int,height:int,text:str='',fg='black',bg='white',font=('微软雅黑',12),anchor='nw')

- pos::位置
- width::宽度
- height::高度
- text::初始文字
- fg::文字颜色
- bg::背景颜色
- font::字体
- anchor::对齐方向

绘制一个单行输入框。这是一个伪绘制组件，其实就是简化了Entry控件的导入。

通过`entry.get()`获取值。

### return: entry

---

### add_separate(self,pos:tuple,width:int,direction='x',fg='grey',anchor='nw')

- pos::位置
- width::长度
- direction::方向。“x”或“y”（横向 或 纵向）
- fg::颜色
- anchor::对齐方向

绘制一条分割线。

### return: separate

---

### add_radiobutton(self,pos:tuple,width,text='',choices=('choose me'),fg='black',bg='white',font=('微软雅黑',12),command=None,anchor='nw')

- pos::位置
- width::整体宽度
- text::单选框文本提示
- choices::选项（list, set, map...）
- fg::文本和边框颜色
- bg::选项背景色
- font::字体
- command::回调函数，有并且仅有一个参数，即该按钮所显示的文本
- anchor::对齐方向

绘制一个单选框，竖式排列。

### return: text, choices_text_list, choices_back

> text::文本提示画布对象
>
> choices_text_list::可选框的文本画布对象
>
> choices_back::可选框的背景方框画布对象

---

### add_link(self,pos:tuple,text,url,fg='#50B0F4',font=('微软雅黑',12),anchor='nw')

- pos::位置
- text::链接文本
- url::链接
- fg::文本颜色
- font::字体
- anchor::对齐方向

绘制一个超链接文本。

### return: link

---

### add_waitbar1(self,pos:tuple,fg='blue',bg='',okfg='lightgreen',okbg='',bd=2,r=20)

- pos::位置
- fg::边框颜色
- bg::内部填充颜色
- okfg::完成时边框颜色
- okbg::完成时内部填充颜色
- bd::外框宽度
- r::半径

绘制一个扇形等待框。

### return: waitbar1,ok

> waitbar1::该画布对象
>
> ok::停止等待动画的函数。当你完成你需要等待的任务后，你可以调用此函数，停止等待动画

---

### add_labelframe(self,widgets:tuple=(),title='',fg='#A8A8A8',bg=''）

- widgets::需要标题框囊括的画布对象
- title::标题
- fg::边框及标题颜色
- bg::背景色

绘制一个标题框，以包含所制定的所有画布对象

### return: label,frame

> label::标题文本
>
> frame::边框画布对象

---

### add_waitbar2(self,pos:tuple,width:int=200,fg='grey',bg='white',okcolor='lightgreen')

- pos::位置
- width::宽度
- fg::点状颜色
- bg::背景颜色
- okcolor::完成时背景填充颜色

绘制一个点状运动的等待框

### return: back,balls:list,stop

> back::背景矩形画布对象
>
> balls::五个圆形画布对象的列表
>
> stop::停止等待动画的函数。当你完成你需要等待的任务后，你可以调用此函数，停止等待动画