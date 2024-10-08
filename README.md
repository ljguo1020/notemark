# notemark (笔记标注)

## 安装
将此文件夹中 `notemark.sty` 放到你的项目文件夹内即可. (目前仅支持 texlive 2024, 后续做兼容)

## 使用
导言区载入 `notemark`
```tex
\usepackage{notemark}
```

### 宏包选项
`notemark` 有 2 个选项，作用如下
- `debug`, 用于观察各组件的间距, 调试使用
- `disable`, 用于清除 `notemark` 的效果

### 宏包命令
#### `\declarenotemark[<options>]{<mark name>}{<separator>}[<options>]`
第一个参数和第四个参数最终会合并成一个参数，只是为了兼容.

第二个参数接受一个命令名,

第三个参数用于定义分割符,
```tex
\declarenotemark\underlinenotemark{\color{red}\hrulefill}[color = red]
```
最终定义出来的 markcommand 均接受三个参数，使用方法为 `\underlinenotemark[<options>]{text}{mark}`

在第三个参数中，`notemark` 向外暴露了一个参数 `\notewidth`, 代表所标记的文字长度.

所以，如下定义也是合理的
```tex
\declarenotemark\underline@notemark@with@tikz{%
  \tikz[] \draw[color = red] (0,0) --++ (\notewidth, 0);
}[below-skip = 1pt, color = red, above-skip = 1pt]
```
关于 `options`, 如下记录
- `above-skip`, 分隔符与上方文字间距, 默认值 1pt.
- `below-skip`, 分隔符与下方文字间距, 默认值 1pt.
- `font`, mark 文字的字体, 默认 `\footnotesize`.
- `color`, mark 文字的颜色,  默认 `black`.


#### `\listofmarks` 用于展示所有的 mark.
...
---
