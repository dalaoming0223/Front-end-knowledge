# 【Emmet语法】

`Emmet` 语法的前身是 `Zen coding`，它使用缩写，来提高 `html/css` 的编写速度,，`VSCode` 内部已经集成该语法。

- 快速生成 HTML 结构语法
- 快速生成 CSS 样式语法

## 快速生成HTML结构语法

- 生成标签直接输入标签名按 tab 键即可，比如 `div` 然后 tab 键， 就可以生成 `<div><div>`
- 如果想要生成多个相同标签加上 `*` 就可以了，比如 `div*3` 就可以快速生成 3 个 `div`
- 如果有父子级关系的标签，可以用 `>` 比如 `ul>li` 就可以了
- 如果有兄弟关系的标签，用 `+` 就可以了 比如 `div+p`
- 如果生成带有 `类名` 或者 `id` 名字的标签， 直接写 `标签.demo` 或者 `标签#demo` 再按下 tab 键就可以了
- 如果生成的事物有顺序，可以用自增符号 `$`
- 如果想要在生成的标签内部写内容可以用 `{}` 表示

## 快速生成CSS样式语法

CSS 基本采取简写形式即可。

- 比如 `w200` 按 tab 可以 生成 `width: 200px;`
- 比如 `lh26px` 按 tab 可以生成 `line-height: 26px;`

```html
<!doctype html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Emmet语法之快速生成CSS样式语法</title>
    <style>
        .one {
            /* tac */
            text-align: center;
            /* ti2e */
            text-indent: 2em;
            /* w */
            /* width: ; */
            /* h */
            /* height: ; */
            /* w24 */
            width: 24px;
            /* h24 */
            height: 24px;
            /* tdn */
            text-decoration: none;
        }
    </style>
</head>

<body>

</body>

</html>
```

## 快速格式化代码

`VSCode` 快速格式化代码：Shift + Alt + F。

`WebStorm` 快速格式化代码：Ctrl + Alt + L。