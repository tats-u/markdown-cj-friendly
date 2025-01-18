# CommonMark CJK-friendly Amendments Specification

CommonMark issue: https://github.com/commonmark/commonmark-spec/issues/650

## 2. Preliminaries 

### 2.1 Characters and lines

A <a href="#cjk-code-point-without-variation-selector" id="cjk-code-point-without-variation-selector">CJK code point without variation selector</a> is an Unicode code point that meets _at least one_ of the following criteria:

- Meets _both_ of the following criteria:
  - [UAX #11 East Asian Width](https://www.unicode.org/reports/tr11/) category is either `W`, `F`, or `H`
  - Not "fully-qualified emoji" defined in [UTS #51 Unicode Emoji](https://www.unicode.org/reports/tr51/#def_qualified_emoji_character)
- [UAX #24 Unicode Script Property](https://www.unicode.org/reports/tr24/) is Hangul

An <a href="#ivs" id="ivs">IVS (Ideographic Variation Selector/Sequence)</a> is an Unicode code point in the Variation Selectors Supplement Block (U+E0100–U+E01EF).

A <a href="#svs-that-can-follow-cjk" id="svs-that-can-follow-cjk">SVS (Standard Variation Selector/Sequence) that can follow CJK</a> is an Unicode code point in U+FE00–U+FE02 or U+FE0E as of Unicode 16. [^svs-range]

[^svs-range]: The range except for U+FE0E is computed from https://www.unicode.org/Public/16.0.0/ucd/StandardizedVariants.txt (as of Unicode 16) by extracting those that can follow CJK characters.

## 6. Inlines

### 6.2 Emphasis and strong emphasis

> [!NOTE]
> The ***bold italic*** means the modified part.

A [left-flanking delimiter run](#left-flanking-delimiter-run) is a [delimiter run](https://spec.commonmark.org/0.31.2/#delimiter-run) that is (1) not followed by [Unicode whitespace](https://spec.commonmark.org/0.31.2/#unicode-whitespace), and either (2a) not followed by a [Unicode punctuation character](https://spec.commonmark.org/0.31.2/#unicode-punctuation-character), or (2b) followed by a [Unicode punctuation character](https://spec.commonmark.org/0.31.2/#unicode-punctuation-character) and preceded by [Unicode whitespace](https://spec.commonmark.org/0.31.2/#unicode-whitespace)***,*** a [Unicode punctuation character](https://spec.commonmark.org/0.31.2/#unicode-punctuation-character)***, a [CJK code point without variation selector](#cjk-code-point-without-variation-selector), an [IVS (Ideographic Variation Selector/Sequence)](#ivs), or a [SVS that can follow CJK](#svs-that-can-follow-cjk) preceded by a [CJK code point without variation selector](#cjk-code-point-without-variation-selector)***. For purposes of this definition, the beginning and the end of the line count as [Unicode whitespace](https://spec.commonmark.org/0.31.2/#unicode-whitespace).

A right-flanking delimiter run is a [delimiter run](https://spec.commonmark.org/0.31.2/#delimiter-run) that is (1) not preceded by [Unicode whitespace](https://spec.commonmark.org/0.31.2/#unicode-whitespace), and either (2a) not preceded by a [Unicode punctuation character](https://spec.commonmark.org/0.31.2/#unicode-punctuation-character), or (2b) preceded by a [Unicode punctuation character](https://spec.commonmark.org/0.31.2/#unicode-punctuation-character) and followed by [Unicode whitespace](https://spec.commonmark.org/0.31.2/#unicode-whitespace)***,*** a [Unicode punctuation character](https://spec.commonmark.org/0.31.2/#unicode-punctuation-character)***, or a [CJK code point without variation selector](#cjk-code-point-without-variation-selector)***. For purposes of this definition, the beginning and the end of the line count as [Unicode whitespace](https://spec.commonmark.org/0.31.2/#unicode-whitespace).

## Tips for Implementers

- [CJK code point without variation selector](#cjk-code-point-without-variation-selector) contains the following characters:
  - 〰 (U+3030)
  - 〽 (U+303D)
  - 🈂 (U+1F202)
  - 🈷 (U+1F237)
  - ㊗ (U+3297)
  - ㊙ (U+3299)
- The East Asian Width of IVS and SVS is `A`.
- The East Asian Width of characters whose Script is Hangul can be `N` (U+1160–U+11FF). However, there are no characters whose Script is Hangul and East Asian Width is `A` or `Na` as of Unicode 16.
- The East Asian Width of unassigned characters (e.g. U+3097 and U+2FFFF) is undefined. If you want to generate ranges for [CJK code points without variation selector](#cjk-code-point-without-variation-selector) and pass them to e.g. an `if` statement as a condition expression concatenated with `||`, you can treat unassigned characters as CJK to concatenate 2 separated ranges (by this you can reduce product terms) or non-CJK. It is up to you implementers to decide how to treat unassigned characters whose East Asian Width is undefined.

## Unicode data list

| Data name | Latest | Unicode 16 |
| --- | --- | --- |
| East Asian Width | https://www.unicode.org/Public/UCD/latest/ucd/EastAsianWidth.txt | https://www.unicode.org/Public/16.0.0/ucd/EastAsianWidth.txt |
| Script | https://www.unicode.org/Public/UCD/latest/ucd/Scripts.txt | https://www.unicode.org/Public/16.0.0/ucd/Scripts.txt |
| Block | https://www.unicode.org/Public/UCD/latest/ucd/Blocks.txt | https://www.unicode.org/Public/16.0.0/ucd/Blocks.txt |
| Characters followed by SVS | https://www.unicode.org/Public/UCD/latest/ucd/StandardizedVariants.txt | https://www.unicode.org/Public/16.0.0/ucd/StandardizedVariants.txt |
| Fully-qualified Emojis (without ZWJ) | https://unicode.org/Public/emoji/latest/emoji-sequences.txt | https://unicode.org/Public/16.0.0/emoji/emoji-sequences.txt |
| Emoji qualification test | https://unicode.org/Public/emoji/latest/emoji-test.txt | https://unicode.org/Public/16.0.0/emoji/emoji-test.txt |
