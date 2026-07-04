# Codex Talk Lecture Note Template

このリポジトリは，集中講義で記録した手書きノートを，Codex と共同で TeX 化するためのテンプレートである。
目的は，集中講義で記録された日程，講義回，節題，話題の流れ，主張，記号，引用箇所，参考文献対応を失わず，手書きノートに書かれた内容を本文として読める PDF にすることである。
完成版の主眼は，手書きノートの内容をすべて TeX 打ちすることであり，講義内容の要約や教科書風の再構成ではない。
単発講演や連続講演にも転用できるが，運用上の判断は集中講義記録を主対象として行う。

このテンプレートは `codex-study-note-template` と並列に使う。
`codex-study-note-template` は教科書・講義ノートをもとに完成版だけで読める勉強ノートを作るためのテンプレートであり，このテンプレートは集中講義の記録を主対象にする。

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
2. `PROJECT_PROFILE.md` に，集中講義名，講師，開催日程，完成版の目的，資料優先順位を記入する。
3. 手書きノートを `sources/handwritten_notes/` に置く。
4. 板書写真を `sources/board_photos/` に置く。
5. スライドを `sources/slides/` に置く。
6. 配布資料を `sources/handouts/` に置く。
7. 開催情報，講演概要，プログラムなどを `sources/event_info/` に置く。
8. `SOURCE_INDEX.md` に資料一覧を登録する。
9. `SESSION_INDEX.md` に日程・講義回・話題ブロックと反映先を記録する。
10. 最初の Codex 作業では，次のように依頼する。

```text
WORKFLOW_STEPS.md を入口として読み，PROJECT_PROFILE.md, TALK_RECORD_POLICY.md, SOURCE_CAPTURE_POLICY.md, REFERENCE_CITATION_POLICY.md, SOURCE_INDEX.md, SESSION_INDEX.md, HANDWRITTEN_REFERENCE_INDEX.md, CODEX_REFERENCE_CANDIDATES.md, CLAIM_REFERENCE_MAP.md を確認してから，手書きノートを入口に参考文献候補と講義中の主張を整理してください。
```

## フォルダ構成

- `WORKFLOW_STEPS.md`: Codex が最初に読む再現可能な作業手順。
- `PROJECT_PROFILE.md`: 集中講義ごとの設定。
- `TALK_RECORD_POLICY.md`: 集中講義記録として本文を作る方針。
- `SOURCE_CAPTURE_POLICY.md`: 手書きノート，板書，スライド，配布資料から情報を拾う方針。
- `REFERENCE_CITATION_POLICY.md`: 参考文献候補，引用箇所，定理番号対応を扱う方針。
- `SOURCE_INDEX.md`: 入力資料の台帳。
- `SESSION_INDEX.md`: 日程・講義回・話題ブロックの対応表。
- `HANDWRITTEN_REFERENCE_INDEX.md`: 手書きノートから拾った参考文献候補。
- `CODEX_REFERENCE_CANDIDATES.md`: Codex が講義資料の外から提案した参考文献候補。
- `CLAIM_REFERENCE_MAP.md`: 講義中の主張と参考文献の対応表。
- `NOTATION_CONFLICTS.md`: 記号衝突と採用記法の記録。
- `SOURCE_GAPS.md`: 判読不能，資料不足，引用未特定，資料間衝突の記録。
- `TERM_DICTIONARY.md`: 用語辞書。
- `TERM_DICTIONARY_CANDIDATES.md`: ユーザー確認前の用語候補。
- `REVISION_CANDIDATES.md`: 本文へ反映するか検討中の修正文候補。
- `GIT_WORKFLOW.md`: Git 運用方針。
- `main_final.tex`: 完成版記録の親ファイル。
- `preemble.tex`: プリアンブル。定理環境，参照マクロ，資料参照マクロを定義する。
- `final/`: 完成版記録の LaTeX 本文。
- `sources/handwritten_notes/`: 手書きノート。
- `sources/board_photos/`: 板書写真。
- `sources/slides/`: スライド。
- `sources/handouts/`: 配布資料。
- `sources/event_info/`: 講演概要，プログラム，開催情報。
- `references/pdfs/`: 補助参考文献 PDF。
- `references/REFERENCE_INDEX.md`: 参考文献台帳。
- `references/notes/`: 参考文献ごとの確認メモ。
- `work/`: OCR，画像抽出，文字起こし，確認用メモなどの作業場所。

## 基本方針

- 手書きノートを最優先資料にし，書かれている内容をすべて TeX 化することを基本作業にする。
- 集中講義の日程，講義回，節題，話題ブロックの順序を保存し，教科書風の章構成へ勝手に組み替えない。
- 節題，小見出し，用語，英語表記は手書きノートを優先し，手書きノートで英語の語は無理に日本語へ訳さない。
- 板書写真，スライド，配布資料は，手書きノートの記録を確認・補強するために使う。
- ユーザーが `sources/` や `references/` に入れた資料は，台帳化した上で対象範囲に関係する限り積極的に使う。
- 手書きノートと配布資料に入っている参考文献を最優先の引用候補にする。
- 講義内で参照された文献を丁寧に拾い，対応する定理番号，命題番号，節番号，ページ，URL を確認する。
- 参考文献欄には URL または DOI を可能な限り明示し，文献がどのような参考資料かという説明文は原則として書かない。
- 集中講義中に挙げられた参考文献，ユーザーが追加した参考文献，Codex が提案した参考文献は混ぜずに分けて記録する。
- Codex が追加で参考文献を提案する場合は，講義由来の文献と出自を分けて `CODEX_REFERENCE_CANDIDATES.md` に記録する。
- 参考文献を見て証明を補完しない。
- 講義中に記録されていない補題，定理，証明手順を本文へ勝手に追加しない。
- 記号が資料間で衝突する場合は，講義中の記法を優先しつつ，参考文献側の記法との差分を `NOTATION_CONFLICTS.md` に残す。
- Codex 提案参考文献は，引用未特定，記号衝突，標準出典確認，書誌情報確認の補助として使い，講義中に実際に参照された文献として扱わない。
- 一般的に飛ばされている背景や行間は，本文の主線を拡張せず，補足程度の引用に留める。
- 参考文献確認は，手書きノートを TeX 化した後で，証明や紹介された主張・事実が文献のどこにあるかを補足するために行う。
- 講義中の主張と参考文献の主張は，完全一致，記号違い，仮定違い，類似，未確定を区別する。
- 定理番号，ページ番号，URL は推測で書かない。
- 権利上共有できない PDF，写真，手書きノート，配布資料はテンプレート配布物には含めない。

## ビルド

```sh
latexmk -g -dvi -interaction=nonstopmode main_final.tex
```

成功すると `main_final.pdf` と `main_final.synctex.gz` が生成される。
完成 PDF は表紙を置かず，小さめのタイトルと目次から始める。
本文は大きな章見出しを使わず，参考講義ノートのように概要と番号付き節を続ける。
TeX 本文を編集した場合は，対象話題ブロックごとにビルドする。

## Git 運用

このテンプレートは Git 管理して使う。
作業開始時には `git status --short --branch`，作業後には `git diff` と `git diff --check` を確認する。
本文改訂，方針変更，台帳更新，参考文献確認は commit 単位を分ける。
詳細は `GIT_WORKFLOW.md` に従う。
