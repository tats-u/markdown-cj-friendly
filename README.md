# Markdown packages in CommonMark compatible with Chinese and Japanese

## Packages / パッケージ一覧 / 包裹

- `markdown-it-cj-friendly` [![Version](https://img.shields.io/npm/v/markdown-it-cj-friendly)](https://npmjs.com/package/markdown-it-cj-friendly)

## Planned / 予定 / 计划

- Drop-in replacement packages for micromark

## Problem / 問題 / 问题

CommonMark has a problem that the following emphasis marks `**` are not recognized as emphasis marks in Japanese and Chinese.

<span lang="ja">CommonMarkには、日本語・中国語内の次のような強調記号(`**`)が強調記号として認識されない問題があります。</span>

<span lang="zh-Hans-CN">CommonMark存在以下问题：在中文和日语文本中，强调标记**不会被识别为强调标记。</span>

```md
**このアスタリスクは強調記号として認識されず、そのまま表示されます。**この文のせいで。

**该星号不会被识别，而是直接显示。**这是因为它没有被识别为强调符号。
```

This problem occurs because the character just inside the `**` is a (Japanese or Chinese) punctuation mark (。) and the character just outside is not a space or punctuation mark.

<span lang="ja">これが起こった原因は、終了側の`**`のすぐ内側が約物（。）、かつ外側が約物や空白以外の文字であるためです。</span>

<span lang="zh-Hans-CN">这个问题是因为在`**`的结束部分，内侧字符是中文或日文的标点符号（。），而外侧字符不是空格或标点符号。</span>

Of course, not only the end side but also the start side has the same issue.

<span lang="ja">もちろん終了側だけでなく、開始側も同様の問題が存在します。</span>

<span lang="zh-Hans-CN">当然，不仅是结束侧，开始侧也存在同样的问题。</span>


## Submit an issue or PR / Issue・PRの投稿 / 提出一个 issue 或 PR

Please submit an issue or PR in English or Japanese. English is recommended.

<span lang="ja">Issue・PRは英語か日本語で投稿してください。英語を推奨します。</span>

<span lang="zh-Hans-CN">请用英语或日语提交问题或 PR。建议使用英语。</span>
