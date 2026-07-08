# Codex Talk Lecture Note Template

このリポジトリは，集中講義・連続講演・単発講演で記録した手書きノートを，Codex と共同で TeX 化するためのテンプレートである。
目的は，講義中に記録された日程，講義回，節題，話題の流れ，主張，記号，引用箇所，参考文献対応を失わず，手書きノートに書かれた内容を自己完結した本文として読める PDF にすることである。

## 配布 URL

- テンプレート: <https://github.com/syzhmr/codex-talk-lecture-note-template>
- 関連テンプレート: <https://github.com/syzhmr/codex-study-note-template>
- 推奨 devcontainer: <https://github.com/syzhmr/LaTeX/tree/main/.devcontainer>

SSH で取得する場合:

```sh
git clone git@github.com:syzhmr/codex-talk-lecture-note-template.git
```

## 使い始め

1. このフォルダ全体を新しいプロジェクト名へコピーする。
2. `PROJECT_PROFILE.md` に，講義名，実施大学，時期，講演者，ノート作成者，開催日程，完成版の目的，資料優先順位を記入する。
3. 手書きノートを `sources/handwritten_notes/` に置く。
4. 板書写真，スライド，配布資料，開催情報があれば `sources/` 以下の対応ディレクトリに置く。
5. 参考文献 PDF は `references/pdfs/` に置く。
6. `WORK_LEDGER.md` の入力資料，セッション，話題ブロック，作業キューをプロジェクトに合わせて埋める。
7. 最初の Codex 作業では次のように依頼する。

```text
WORKFLOW_STEPS.md を入口として読み，PROJECT_PROFILE.md，NOTE_POLICY.md，WORK_LEDGER.md，TERM_DICTIONARY.md を確認してから，手書きノートを入口にスモールステップで対象範囲を整理してください。
```

## フォルダ構成

- `WORKFLOW_STEPS.md`: Codex が最初に読む再現可能な作業手順。
- `PROJECT_PROFILE.md`: 講義・講演ごとの設定。
- `NOTE_POLICY.md`: 本文作成の品質基準とスモールステップ。
- `WORK_LEDGER.md`: 資料台帳，講義回対応，進捗，未解決点，参考文献対応，記号修正をまとめる作業台帳。
- `TERM_DICTIONARY.md`: 採用語，不使用語，未承認候補，表記衝突を管理する用語辞書。
- `LATEX_SOURCE_POLICY.md`: LaTeX ソースの構造・整形方針。
- `GIT_WORKFLOW.md`: Git 運用方針。
- `main_final.tex`: 完成版記録の親ファイル。
- `preemble.tex`: プリアンブル。
- `final/`: 完成版本文。
- `sources/`: 手書きノート，板書写真，スライド，配布資料，開催情報。
- `references/`: 参考文献 PDF，検索用テキスト，参考文献台帳，読解メモ。
- `scripts/`: 参考文献 PDF のテキスト抽出・OCR 用スクリプト。
- `work/`: 画像抽出，文字起こし，確認用メモなどの作業場所。

## 基本方針

- 手書きノートを最優先資料にし，書かれている内容をすべて TeX 化することを基本作業にする。
- 手書きノートは OCR にかけない。本文確定は単ページ画像または元 PDF の該当ページを目視して行う。
- 作業開始時は `WORKFLOW_STEPS.md` 冒頭の「最短チェックリスト」で，作業型，読むファイル，作業キュー，次の Step を固定する。
- 本文整理は `NOTE_POLICY.md` のスモールステップに従い，小ステップを飛ばして完成扱いにしない。
- 1 から本文を作る場合は，本文作成前に目標密度プロファイルを作り，図式，例，注意，Recall，証明，引用，脚注，三点リーダー，アスタリスク標識が落ちていないか loss audit する。
- 全面改訂では，手書きノートの 1 ページ目から 1 ページずつ確認する。複数ページを並べた確認用画像だけを本文反映の根拠にしない。
- 完成 PDF は，この PDF だけで読める講義ノートにする。本文中に「手書きノート p.X」「手書きノートでは」「記録として」「未確認」などの作業用ラベルを出さない。
- 集中講義の日程，講義回，節題，話題ブロックの順序を保存し，教科書風の章構成へ勝手に組み替えない。
- 数学的に自然に見える補いであっても，手書きノートにない主張，理由，証明範囲，接続文，抽象化表現を本文へ足さない。
- 参考文献は，講義中の主張との対応，引用箇所，記号衝突，訳語候補，書誌情報の確認に使う。手書きノートにない証明や背景定理を本文へ補完するためには使わない。
- 定理，命題，補題，claim などに対する証明本文または sketch が手書きにある場合は，本文でも `proof` 環境を使う。
- 可換図式，局所化図式，体の塔，Hasse 図は省略せず，`tikzcd`，`matrix of math nodes`，直接 `\node` と `\path` による配置の順で TeX 化を検討する。生成画像では代替しない。
- チルダ系の `\tilde{}`，`\widetilde{}`，`\sim` と，ハット系の `\hat{}`，`\widehat{}` は個別に照合する。
- `レポート問題`，`これを示せ`，欄外メモ，矢印，引き出し線は，画像上の位置から作用範囲を確認し，不明な場合は本文で広げず `WORK_LEDGER.md` に残す。

## PDF 冒頭

完成 PDF の冒頭は，表紙を置かず，次の順に置く。
テンプレートには具体名を入れず，プロジェクトごとに埋める。

```text
講義・講演名
実施大学・会場
時期
講演者
ノート
```

各日の最初のセクション見出しの直前には `\recorddate{YYYY年M月D日}` で日付を表示する。
日付は目次へ入れず，太字にしない。

## ビルド

```sh
latexmk -g -dvi -interaction=nonstopmode main_final.tex
```

成功すると `main_final.pdf` と `main_final.synctex.gz` が生成される。
`main_final.synctex.gz` は TeX ソースと PDF の対応確認に使うため削除しない。
`main_final.log` はビルド確認に使うため保存する。
TeX 本文を編集した場合は，対象話題ブロックごとにビルドする。
