---
title: Expressive Code 示例
published: 2024-04-10
description: 使用 Expressive Code 在 Markdown 中展示代码块的效果。
tags: [Markdown, 博客, 演示]
category: 示例
draft: false
---

在这里，我们将探索使用 [Expressive Code](https://expressive-code.com/) 展示代码块的效果。提供的示例基于官方文档，你可以参考官方文档了解更多详情。

## Expressive Code

### 语法高亮

[语法高亮](https://expressive-code.com/key-features/syntax-highlighting/)

#### 常规语法高亮

```js
console.log('这段代码有语法高亮！')
```

#### 渲染 ANSI 转义序列

```ansi
ANSI 颜色：
- 常规：[31m红色[0m [32m绿色[0m [33m黄色[0m [34m蓝色[0m [35m品红[0m [36m青色[0m
- 加粗：[1;31m红色[0m [1;32m绿色[0m [1;33m黄色[0m [1;34m蓝色[0m [1;35m品红[0m [1;36m青色[0m
- 变暗：[2;31m红色[0m [2;32m绿色[0m [2;33m黄色[0m [2;34m蓝色[0m [2;35m品红[0m [2;36m青色[0m

256 色（显示颜色 160-177）：
[38;5;160m160 [38;5;161m161 [38;5;162m162 [38;5;163m163 [38;5;164m164 [38;5;165m165[0m
[38;5;166m166 [38;5;167m167 [38;5;168m168 [38;5;169m169 [38;5;170m170 [38;5;171m171[0m
[38;5;172m172 [38;5;173m173 [38;5;174m174 [38;5;175m175 [38;5;176m176 [38;5;177m177[0m

全 RGB 颜色：
[38;2;34;139;34m森林绿 - RGB(34, 139, 34)[0m

文本格式：[1m加粗[0m [2m变暗[0m [3m斜体[0m [4m下划线[0m
```

### 编辑器和终端框架

[编辑器和终端框架](https://expressive-code.com/key-features/frames/)

#### 代码编辑器框架

```js title="my-test-file.js"
console.log('标题属性示例')
```

---

```html
<!-- src/content/index.html -->
<div>文件名注释示例</div>
```

#### 终端框架

```bash
echo "这个终端框架没有标题"
```

---

```powershell title="PowerShell 终端示例"
Write-Output "这个有一个标题！"
```

#### 覆盖框架类型

```sh frame="none"
echo "看，没有框架！"
```

---

```ps frame="code" title="PowerShell Profile.ps1"
# 如果不覆盖，这原本会是一个终端框架
function Watch-Tail { Get-Content -Tail 20 -Wait $args }
New-Alias tail Watch-Tail
```

### 文本和行标记

[文本和行标记](https://expressive-code.com/key-features/text-markers/)

#### 标记整行和行范围

```js {1, 4, 7-8}
// 第 1 行 - 通过行号指定
// 第 2 行
// 第 3 行
// 第 4 行 - 通过行号指定
// 第 5 行
// 第 6 行
// 第 7 行 - 通过范围 "7-8" 指定
// 第 8 行 - 通过范围 "7-8" 指定
```

#### 选择行标记类型 (mark, ins, del)

```js title="line-markers.js" del={2} ins={3-4} {6}
function demo() {
  console.log('这行被标记为已删除')
  // 这行和下一行被标记为已插入
  console.log('这是第二行已插入的代码')

  return '这行使用中性的默认标记类型'
}
```

#### 为行标记添加标签

```jsx {"1":5} del={"2":7-8} ins={"3":10-12}
// labeled-line-markers.jsx
<button
  role="button"
  {...props}
  value={value}
  className={buttonClassName}
  disabled={disabled}
  active={active}
>
  {children &&
    !active &&
    (typeof children === 'string' ? <span>{children}</span> : children)}
</button>
```

#### 在单独的行上添加长标签

```jsx {"1. 在这里提供 value 属性：":5-6} del={"2. 移除 disabled 和 active 状态：":8-10} ins={"3. 添加此项以在按钮内渲染子元素：":12-15}
// labeled-line-markers.jsx
<button
  role="button"
  {...props}

  value={value}
  className={buttonClassName}

  disabled={disabled}
  active={active}
>

  {children &&
    !active &&
    (typeof children === 'string' ? <span>{children}</span> : children)}
</button>
```

#### 使用类 diff 语法

```diff
+这行将被标记为已插入
-这行将被标记为已删除
这是一行普通的文本
```

---

```diff
--- a/README.md
+++ b/README.md
@@ -1,3 +1,4 @@
+这是一个实际的 diff 文件
-所有内容都将保持不变
 空格也不会被移除
```

#### 将语法高亮与类 diff 语法结合使用

```diff lang="js"
  function thisIsJavaScript() {
    // 整个块都以 JavaScript 高亮显示，
    // 并且我们仍然可以向其添加 diff 标记！
-   console.log('要移除的旧代码')
+   console.log('闪亮的新代码！')
  }
```

#### 标记行内的单个文本

```js "given text"
function demo() {
  // 标记行内的任何给定文本
  return '支持给定文本的多次匹配';
}
```

#### 正则表达式

```ts /ye[sp]/
console.log('单词 yes 和 yep 将被标记。')
```

#### 转义前斜杠

```sh /\/ho.*\//
echo "测试" > /home/test.txt
```

#### 选择行内标记类型 (mark, ins, del)

```js "return true;" ins="inserted" del="deleted"
function demo() {
  console.log('这是插入和删除的标记类型');
  // return 语句使用默认标记类型
  return true;
}
```

### 自动换行

[自动换行](https://expressive-code.com/key-features/word-wrap/)

#### 为每个代码块配置自动换行

```js wrap
// 自动换行示例
function getLongString() {
  return '这是一个非常长的字符串，除非容器非常宽，否则它很可能无法放入可用空间中'
}
```

---

```js wrap=false
// wrap=false 示例
function getLongString() {
  return '这是一个非常长的字符串，除非容器非常宽，否则它很可能无法放入可用空间中'
}
```

#### 配置换行行的缩进

```js wrap preserveIndent
// preserveIndent 示例（默认启用）
function getLongString() {
  return '这是一个非常长的字符串，除非容器非常宽，否则它很可能无法放入可用空间中'
}
```

---

```js wrap preserveIndent=false
// preserveIndent=false 示例
function getLongString() {
  return '这是一个非常长的字符串，除非容器非常宽，否则它很可能无法放入可用空间中'
}
```
