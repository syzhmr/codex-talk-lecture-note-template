# 完成版本文

完成版の集中講義記録の LaTeX 本文を置く。

- `talk01.tex`: 集中講義の親ファイル。必要に応じて `day01.tex` などへ分ける。
- `talk01/01-overview.tex`: 話題ブロック単位の本文ファイル。
- `references.tex`: 完成 PDF 末尾の参考文献欄。

完成版は article 型の講義ノート体裁にし，大きな章見出しは使わない。
最初の概要は `\recordintro{概要}` を使い，続く講義回や話題ブロックは `\section`，`\subsection` で整理する。

集中講義として使う場合は，必要に応じて次のように増やす。

```text
final/
  day01.tex
  day01/
    lecture01.tex
    lecture02.tex
  day02.tex
```

広い範囲を整理する場合でも，作業と査読は話題ブロック単位で行う。
