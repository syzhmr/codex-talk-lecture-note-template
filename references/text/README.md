# 参考文献PDFの検索用テキスト

このディレクトリには，`references/pdfs/` の PDF から作った検索用テキストを置く。
対象は参考文献 PDF だけである。
手書きノートは OCR にかけず，本文確定は単ページ画像または元 PDF の該当ページを目視して行う。

## 生成

通常のテキスト抽出を行う。

```sh
scripts/extract-reference-text.sh
```

特定の PDF だけ処理する。

```sh
scripts/extract-reference-text.sh references/pdfs/example.pdf
```

既存出力が新しくても作り直す。

```sh
scripts/extract-reference-text.sh --force references/pdfs/example.pdf
```

スキャン PDF を OCR する。

```sh
scripts/ocr-reference-text.sh references/pdfs/example-scanned.pdf
```

横書き日本語 PDF を OCR する。

```sh
scripts/ocr-reference-text.sh --lang jpn references/pdfs/example-japanese.pdf
```

英日混在 PDF を OCR する。

```sh
scripts/ocr-reference-text.sh --lang jpn+eng references/pdfs/example-mixed.pdf
```

数式主体の英語 PDF は，LaTeX 直下に Nougat 補助スクリプトがある場合だけ `.mmd` も作る。

```sh
../tools/nougat/nougat-pdf-to-mmd.sh --out references/text references/pdfs/example.pdf
```

Nougat 出力の欠落や反復崩れを確認する。

```sh
../tools/nougat/check-mmd-quality.sh references/text/*.mmd
```

## 運用

- `*.txt` は `pdftotext` で抽出した検索用テキスト。
- `*.ocr.txt` はスキャン PDF から Tesseract で作った検索用テキスト。
- `*.mmd` は Nougat などで作った数式寄りの変換結果。
- OCR と Nougat は参考文献 PDF の検索補助であり，手書きノートには使わない。
- `*.txt` と `*.ocr.txt` 内のページ番号は PDF 上のページ番号であり，印刷ページ番号とは一致しないことがある。
- 本文，小さめの数式，定理番号，ページ見出し，記号確認は抽出テキスト，OCR テキスト，または `.mmd` を入口にしてよい。
- 大きい表示数式，グラフ，可換図式，体拡大の Hasse 図，引用に関わる符号は，検索用テキストだけで確定せず，原典 PDF の該当ページ画像で確認する。
- 読解結果，本文との対応，OCR の限界，画像確認したページは `references/notes/`，`references/REFERENCE_INDEX.md`，`WORK_LEDGER.md` の必要箇所に記録する。

検索例:

```sh
rg -n -C 2 "keyword|theorem|\\\\mathbb" references/text
```
