# Markdownlint规则

本文档为terraform-provider-huaweicloud仓库使用的markdownlint规则的说明。

## MD001 - 标题级别一次只能增加一级

错误示例：

```markdown
# 一级标题

### 三级标题
```

使用多个标题级别时，嵌套标题一次只允许增加一级。正确示例：

```markdown
# 一级标题

## 二级标题

### 三级标题

#### 四级标题

## 另一个二级标题

### 另一个三级标题
```

## MD003 - 标题样式

本仓库使用的是ATX风格的标题样式（左侧井字符标识）

```markdown
# ATX风格标题
```

## MD004 - 无序列表样式

markdown列表样式提供三种特定的符号（星号、加号、破折号）以表示列表样式，本仓库使用的是sublist风格的列表样式：确保每个子列表具有与其父列表不同的一致符号。

说明：以三层为例，最外层缩进使用星号，中间缩进使用加号，最内缩进使用破折号。三层以上循环类推。

```markdown
* 项目1
  + 项目3
    - 项目5
  + 项目4
* 项目2
  + 项目6
```

## MD005 - 同一级别的列表项的缩进需要保持一致

错误示例：

```markdown
* Item 1
  * Nested Item 1
  * Nested Item 2
   * A misaligned item
```

正确示例：

```markdown
* Item 1
  * Nested Item 1
  * Nested Item 2
  * Nested Item 3
```

有序排列的列表标记通常是左对齐的：

```markdown
...
8. Item
9. Item
10. Item
11. Item
...
```

当然此规则还支持列表标记的右对齐：

```markdown
...
 8. Item
 9. Item
10. Item
11. Item
...
```

## MD009 - 行末禁止出现尾随空格

错误示例：

```markdown
描述[2个空格]
```

正确示例：

```markdown
描述[无空格]
```

## MD010 - 禁止使用制表符缩进

制表符在不同的编辑器中呈现的样式不一致，相较空格更难使用，因此禁止在文档的各行中使用制表符缩进。

错误示例：

```markdown
上文

    * 使用制表符缩进的列表项
```

<!-- markdownlint-restore -->

正确示例：

```markdown
上文

  * 使用空格代替制表符进行缩进
```

IDE中支持修改缩进样式，开发者可根据此设置减少该问题的产生。

## MD011 - 禁止使用反向超链接语法

禁止使用语法颠倒的超链接表述（中括号和括号倒置）。语法颠倒的超链接表述不仅无法将链接加入到对应的文本中，也会在显示上输出两组括号。

错误示例：

```markdown
(错误的超链接语法)[https://www.example.com/]
```

交换两组括号即可修复（内容位置不变）。

```markdown
[正确的超链接语法](https://www.example.com/)
```

## MD012 - 禁止出现多个连续的空行

文档中连续的空行所起到的效果等同于单空行，因此在文档中禁止使用多余的空行。

错误示例：

```markdown
上文


下文
```

删除多余的空行以修复该问题。
正确示例：

```markdown
上文

下文
```

注意: 代码块中的多个空行不会触发此规则。

## MD013 - 行宽

文档中各行的内容最大不超过120个字符。
例外：该规则不检查超链接，不必从中切断。

此外，对于部分README文档中的超长文本且无法截断的可通过markdownlint的相关检查开关标签跳过检查。

错误示例：
```
description - (Optional, String) Specifies the description about the APIG application. The description contain a maximum of 255 characters and the angle brackets (< and >) are not allowed. Chinese characters must be in UTF-8 or Unicode format.
```

正确示例：
```
description - (Optional, String) Specifies the description about the APIG application.
  The description contain a maximum of 255 characters and the angle brackets (< and >) are not allowed.
  Chinese characters must be in UTF-8 or Unicode format.
```

## MD018 - 标题的标识符与标题文本之间必须包含空格

错误示例：

```markdown
#标题 1

##标题 2
```

正确示例:

```markdown
# 标题 1

## 标题 2
```

注意: 违反此规则可能导致文本格式呈现不当。

## MD019 - 标题的标识符与标题文本之间不得包含多个空格

错误示例：

```markdown
#  标题 1

##  标题 2
```

正确示例：

```markdown
# 标题 1

## 标题 2
```

结合MD018规则可以很好地检测标题格式。

## MD020 - 封闭的标题样式中标题文本左右需包含空格（内部也会检查）

对于封闭的标题样式，标题文本应包含正确的空格样式：

错误示例：

```markdown
#标题 1#

##标题2##
```

正确示例：

```markdown
# 标题 1 #

## 标题 2 ##
```

## MD021 - 封闭的标题样式中包含连续的空格

同MD019，对于封闭的标题样式，标题文本各处所包含的空格数量不应超过一个：

错误示例：

```markdown
#  标题 1  #

##  标题 2  ##
```

正确示例：

```markdown
# 标题 1 #

## 标题 2 ##
```

## MD022 - 标题应使用空行与其他内容分隔

每个标题的前后都需要使用空行（数量：1）进行分隔。

错误示例：

```markdown
# 标题 1
文本

另一个文本
## 标题 2
```

正确示例：

```markdown
# 标题 1

文本

另一个文本

## 标题 2
```

## MD023 - 标题必须顶格表示

所有标题的标识符都应位于首列，即左侧不包含空格和文本

错误示例：

```markdown
文本

  # 标题
```

正确示例：

```markdown
文本

# 标题
```

## MD024 - 多个标题的内容不得重复

文档中的各标题的内容不重复。

错误示例：

```markdown
# 这是一个标题名称

## 这是一个标题名称
```

正确示例：

```markdown
# 这是一个标题名称

## 这是另一个标题名称
```

例外：应用了siblings_only后，当且仅当标题之间为兄弟关系时，可以包含相同的内容。

```markdown
# Change log

## 1.0.0

### Features

## 2.0.0

### Features
```

## MD025 - 文档中不得包含多个一级标题

一般文档的一级标题用于标识文档的名称，而文档的真实标题目录应从二级标题开始，因此，一级标题在一个文档中只应包含一个。

错误示例：

```markdown
# 一个一级标题

# 另一个一级标题
```

正确示例：

```markdown
# 文档名

## 标题

## 另一个标题
```

## MD026 - 文档的标题末尾禁止包含标点符号

任何的文档标题结尾都不应包含标点符号

```markdown
# This is a heading.
```

To fix this, remove the trailing punctuation:

```markdown
# This is a heading
```

注意：问号（？）在默认情况下是允许的，一般用于FAQ文档的标题内容。

## MD027 - 块引用标识符（>）后禁止包含多个空行

错误示例：

```markdown
>  错误的文本缩进
>  前方缩进应该只有一个
```

正确示例：

```markdown
> 正确的文本缩进
> 快引用缩进
```

## MD028 - 块引用之间禁止只包含空行

两个不同的块引用之间不可直接使用空行分隔，需包含文本。

错误示例：

```markdown
> 这是一个块引用
> 其后还有另一个块

> 这是一个新的块引用
> 但在某些IDE中，这两个块会被视为一个块
```

正确示例：

```markdown
> 这是一个块引用
> 其后还有另一个块

这个块的内容是:

> 这是一个新的块引用
```

当块引用的两部分内容之间需要使用空行进行分隔时，不可直接使用空行分隔，而是使用一个块引用标识符进行分隔。

正确示例：

```markdown
> 这是一个块引用的上半部分
>
> 这是一个块引用的下半部分
```

## MD029 - 有序列表前缀

有序的列表前缀应当由1开始递增，而非1的前缀开头将触发此规则的警告。
（可通过配置修改为从0开始、从1开始、有序以及全部，这里默认配置为：全部）

从1开始：

```markdown
1. 列表项.
1. 列表项.
1. 结束.
```

有序：

```markdown
1. 列表项.
2. 列表项.
3. 结束.
```

或（也是从0开始；从0开始同从1开始，可以无序）：

```markdown
0. 列表项.
1. 列表项.
2. 结束.
```

当应用全部规则时，上述三种示例都有效且支持以0为前缀的有序列表项进行统一缩进。

```markdown
...
08. 列表项.
09. 列表项.
10. 列表项.
11. 列表项.
...
```

注意：此规则将检查是否出现以下违规的情况，即不正确缩进的代码块出现在两个列表项之间并将列表分成了两个部分。

<!-- markdownlint-disable code-fence-style -->

~~~markdown
1. 列表项1

```text
代码块
```

2. 列表项2
~~~

The fix is to indent the code block so it becomes part of the preceding list
item as intended:

~~~markdown
1. 列表项1

   ```text
   代码块
   ```

2. 列表项2
~~~

## MD030 - 列表标识符后的空格数

列表标识符后的空格数由ul_single、ol_single、ul_multi和ol_multi四个参数配置决定，默认为1个空格。

正确示例：

```markdown
* Foo
* Bar
* Baz

1. Foo
1. Bar
1. Baz

1. Foo
   * Bar
1. Baz
```

## MD031 - 代码块前后需使用空行分隔

错误示例：

````markdown
一段文本
```
代码块
```

```
另一个代码块
```
另一段文本
````

正确示例：

````markdown
一段文本

```
代码块
```

```
另一个代码块
```

另一段文本
````

## MD032 - 列表前后需使用空行分隔

错误示例：

```markdown
一段文本
* 列表项1
* 列表项2

1. 列表项1
2. 列表项2
另一段文本
```

正确示例：

```markdown
一段文本

* 列表项1
* 列表项2

1. 列表项1
2. 列表项2

另一段文本
```

## MD034 - 禁止使用裸链接

所有的链接都需要使用括号包围。

错误示例：

```markdown
详细信息请参考https://www.example.com/.
```

正确示例：

```markdown
详细信息请参考<https://www.example.com/>.
```

或通过代码块封装：

```markdown
`https://www.example.com`
```

也可以使用引号包围链接：

```markdown
"https://www.example.com"
'https://www.example.com'
```

## MD035 - 水平线样式

水平线的样式检查默认为统一风格（文档中所有水平线样式保持统一）

错误示例：

```markdown
文档中使用了多种水平线样式

---

- - -

***

* * *

****
```

正确示例：

```markdown
---

---
```

## MD036 - 禁止使用强调代替标题

Tags: headings, headers, emphasis

禁止使用加粗或斜体（组合也不可以）标记文本以代替标题。

错误示例：

```markdown
**章节一**

章节内容...

_章节二_

章节内容...
```

正确示例：

```markdown
## 章节一

章节内容...

## 章节二

章节内容...
```

## MD037 - 强调内容的左右禁止包含空格

错误示例：

```markdown
这是一个 ** 强调 ** 文本.

这是一个 * 强调 * 文本.

这是一个 __ 强调 __ 文本.

这是一个 _ 强调 _ 文本.
```

正确示例：

```markdown
这是一个 **强调** 文本.

这是一个 *强调* 文本.

这是一个 __强调__ 文本.

这是一个 _强调_ 文本.
```

## MD038 - 反引号块内容首末禁止包含空格

此规则将检查反引号旁是否包含空格：

错误示例：

```markdown
`一些文本 `

` 一些文本`
```

正确示例：

```markdown
`一些文本`
```

例外：当反引号中的文本首末需要嵌入反引号时，需以空格分隔

```markdown
`` `一些文本` ``
```

```markdown
`` ` 一些文本 ``
```

## MD039 - 超链接文本中禁止包含空格

错误示例：

```markdown
[ 一个链接 ](https://www.example.com/)
```

正确示例：

```markdown
[一个链接](https://www.example.com/)
```

## MD041 - 文件中的第一行应是一级标题

每个markdown文档都应该包含一个文档名称，即一级标题。

错误示例：

```markdown
这是一个没有一级标题的文档
```

To fix this, add a top-level heading to the beginning of the file:

```markdown
# 文档名称

这是一个带有一级标题的文档
```

## MD042 - 禁止使用空链接

错误示例：

```markdown
[一个空链接]()
```

```markdown
[一个空片段](#)
```

正确示例：

```markdown
[一个有效链接](https://example.com/)
```

```markdown
[一个有效片段](#fragment)
```

## MD045 - 图像应包含替代文本

由于某些情况下用户无法打开图片，替代文本对于无法看到图像描述内容的用户无疑是友好的。

错误示例：

```markdown
![替代文本](image.jpg)
```

正确示例：

```markdown
![替代文本][ref]

...

[ref]: image.jpg "可选标题"
```

## MD046 - 代码块样式

markdown提供了缩进和围栏两种代码块样式，此规则规定了在同一文档中需要使用相同的（style配置为一致）代码块样式。

<!-- markdownlint-disable code-block-style -->

    一些文本.

        # 缩进代码块样式

    另一些文本.

    ```ruby
    # 围栏代码块样式
    ```

    另一些文本.

<!-- markdownlint-restore -->

terraform-provider-huaweicloud仓库使用统一的围栏式代码块。

## MD047 - 文档以单空行结尾

错误示例：

```markdown
# 标题

此文档没有以换行符结尾.[EOF]
```

正确示例：

```markdown
# 标题

此文档没有以换行符结尾.
[EOF]
```

## MD048 - 代码块围栏样式

markdown提供了波浪号和反引号两种风格的代码块围栏风格，在terraform-provider-huaweicloud仓库中配置了统一样式，
即全文的代码块围栏风格需保持一致，约定为反引号。

错误示例：

````markdown
```ruby
# 代码块
```

~~~ruby
# 代码块
~~~
````

正确示例：

````markdown
```ruby
# 代码块
```

```ruby
# 代码块
```
````
