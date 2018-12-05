---
title: Inside theme showcase
date: 2018-09-05 10:34:24
author: elmore
thumbnail: sample.jpg
tags:
 - Inside
categories:
 - Inside
---

<!-- ## Heading

## h2

### h3

#### h4

##### h5

###### h6 -->

## Image

![space](https://www.nasa.gov/sites/default/files/styles/full_width_feature/public/thumbnails/image/nh-pluto-moonlight.jpg)

### Inline image

Not bad.![yes](https://res.smzdm.com/images/emotions/138.png)

### With link

- Travis CI build status: [![build-img]][inside]
- Lastest release: [![release-img]][release]
- License: [![license-img]](LICENSE)

## List

### Unordered list

- list item
- list item
  - list item
  - list item
    - list item
    - list item
- list item

### Ordered list

1. list item
2. list item
    1. list item
    2. list item
        1. list item
        2. list item
3. list item

### Checklist

- [ ] Get up at 7:00 AM
- [x] Eat breakfast
- [ ] Go to bet before 11:00 PM

## Table

Hear no evil | Speak no evil | See no evil
-|-|-
🙉|🙊|🙈

### Text align

Hear no evil | Speak no evil | See no evil
:-|:-:|-:
🙉|🙊|🙈

### Headless

敲空格，或`&nbsp;`。

```md
 | | &nbsp;
:-:|:-:|:-:
🙉|🙊|🙈
```

 | | &nbsp;
:-:|:-:|:-:
🙉|🙊|🙈

### Long table

Sun With Face|Grinning Face|Smiling Face|Grinning Face With Big Eyes|Smiling Face With Smiling Eyes|Full Moon Face|Grinning Face With Smiling Eyes|Face With Monocle|Cowboy Hat Face|Thinking Face|Face Vomiting
-|-|-|-|-|-|-|-|-|-|-
🌞|😀|☺️|😃|😊|🌝|😄|🧐|🤠|🤔|🤮

## Blockquote

(https://hexo.io/docs/tag-plugins#Block-Quote)

{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}

## Code Block

```typescript
class Utils {
  animate(element: Element, attr: string, change: { from: number, to: number, duration?: number }, onEnd?: () => void) {
    if (change.from === change.to) return;

    if (!change.duration)
      element[attr] = change.to;

    const easing = (t, b, c, d) => c * ((t = t / d - 1) * t * t + 1) + b,
      { from, to } = change,
      during = Math.ceil((change.duration || 300) / 17) || 1;

    let start = 0,
      instance = null;

    step();

    function step() {
      const value = Math.ceil(easing(start, from, to - from, during));

      start++;
      if (start <= during) {
        element[attr] = value;
        instance = requestAnimationFrame(step);
      }
      else {
        if (onEnd) onEnd();
        cancelAnimationFrame(instance);
      }
    }
  }
}
```

### With caption

(https://hexo.io/docs/tag-plugins#Code-Block)

{% codeblock lang:js _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
// [1, 2, 3]
{% endcodeblock %}

## Gist

(https://hexo.io/docs/tag-plugins#Gist)

{% gist 59dd307bb56ef7919cc192aa7b547e27 %}

## JSFiddle

(https://hexo.io/docs/tag-plugins#jsFiddle)

{% jsfiddle elmore/myq6ec0j js,result %}

## <script\> ⚠

对 `<script>` 有特殊处理，旨在解决 json 中包含的 JS 脚本无法执行的问题。

示例：

```html
stars: <span id="stargazers_count"></span>

<script>
fetch('https://api.github.com/repos/elmorec/hexo-theme-inside')
  .then(function(res) { return res.json() })
  .then(function(json) {
    document.getElementById('stargazers_count').innerHTML = json.stargazers_count;
  });
</script>
```

stars: <span id="stargazers_count"></span>

<script>
fetch('https://api.github.com/repos/elmorec/hexo-theme-inside')
  .then(function(res) { return res.json() })
  .then(function(json) {
    document.getElementById('stargazers_count').innerHTML = json.stargazers_count;
  });
</script>

若想兼容最新 ES 语法，需安装 Babel 和 UglifyJs（非必须）。

于根目录（Hexo根目录，非 `themes/inside`）下执行：

```bash
npm install babel-core babel-preset-env uglify-js --save
```

## Canvas ⚠

内置标签，用于满足简单的 canvas 绘图需要。

语法：

```js
{% canvas [width] [height] %}
ctx.fillStyle = 'red';
ctx.fillRect(0, 0, w, h);
{% endcanvas %}
```

`width` 默认 300，`height` 默认 150，作用域内注入了以下变量：

&nbsp; | &nbsp;
-------|--------------
ctx    | 2d 上下文对象
w      | 画布宽度
h      | 画布高度

如：

```js
{% canvas 100 100 %}
const r = w / 2;
ctx.fillStyle = 'antiquewhite';
ctx.arc(r, r, r, 0, Math.PI * 2);
ctx.fill();
{% endcanvas %}
```

{% canvas 100 100 %}
const r = w / 2;
ctx.fillStyle = 'antiquewhite';
ctx.arc(r, r, r, 0, Math.PI * 2);
ctx.fill();
{% endcanvas %}

本文随主题不定期更新。

[inside]: https://github.com/elmorec/hexo-theme-inside
[release]: https://github.com/elmorec/hexo-theme-inside/releases
[build-img]: https://img.shields.io/travis-ci/elmorec/hexo-theme-inside.svg?longCache=true&style=flat-square
[release-img]: https://img.shields.io/github/release/elmorec/hexo-theme-inside.svg?longCache=true&style=flat-square
[license-img]: https://img.shields.io/github/license/elmorec/hexo-theme-inside.svg?longCache=true&style=flat-square

[hexo]: https://hexo.io/
[hexo-generator-feed]: https://github.com/hexojs/hexo-generator-feed

[manifest]: https://www.w3.org/TR/appmanifest/
[workbox]: https://developers.google.com/web/tools/workbox/
[meta-theme-color]: https://developers.google.com/web/fundamentals/design-and-ux/browser-customization/#meta_theme_color_for_chrome_and_opera
