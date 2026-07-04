# 再現可能作業手順

このファイルを Codex 作業の入口にする。
目的は，モデルや実行環境が変わっても，同じ順序で資料を確認し，同じ条件で止まり，同じ形で報告できるようにすることである。

## 0. 入口判定

1. `git status --short --branch` を確認する。
2. ユーザーの依頼を次の型に分ける。
   - 方針変更
   - 資料台帳更新
   - 手書きノート確認
   - 参考文献候補抽出
   - 主張と参考文献の対応付け
   - 本文整理
   - LaTeX 整形
   - 用語・記号確認
   - Git 操作
3. 型に応じて読むファイルを最小化する。
4. 未コミット変更がある場合は，変更元と作業範囲を確認し，無関係な変更を壊さない。
5. プロジェクト固有の前提は `PROJECT_PROFILE.md` で確認する。

## 1. 常に読む

1. `WORKFLOW_STEPS.md`
2. `PROJECT_PROFILE.md`
3. `GIT_WORKFLOW.md`

## 2. 方針変更で読む

1. `README.md`
2. `PROJECT_PROFILE.md`
3. `TALK_RECORD_POLICY.md`
4. `SOURCE_CAPTURE_POLICY.md`
5. `REFERENCE_CITATION_POLICY.md`
6. `LATEX_SOURCE_POLICY.md`
7. `GIT_WORKFLOW.md`
8. `SOURCE_INDEX.md`
9. `SESSION_INDEX.md`
10. `HANDWRITTEN_REFERENCE_INDEX.md`
11. `CLAIM_REFERENCE_MAP.md`
12. `NOTATION_CONFLICTS.md`
13. `SOURCE_GAPS.md`
14. `references/README.md`
15. `references/REFERENCE_INDEX.md`
16. `references/notes/README.md`
17. 用語に関わる場合は `TERM_DICTIONARY.md` と `TERM_DICTIONARY_CANDIDATES.md`
18. 修正文候補に関わる場合は `REVISION_CANDIDATES.md`

方針を改訂するときは，関連方針全体を横断的に読み直し，重複，長文化，役割分担の不明瞭さ，判断順の曖昧さ，停止条件の不足を洗い出す。

## 3. 資料確認で読む

### 手書きノート確認

1. `SOURCE_CAPTURE_POLICY.md`
2. `SOURCE_INDEX.md`
3. `SESSION_INDEX.md`
4. 対象の手書きノート
5. 必要に応じて対象の板書写真，スライド，配布資料
6. `HANDWRITTEN_REFERENCE_INDEX.md`
7. `SOURCE_GAPS.md`

### 参考文献候補抽出

1. `REFERENCE_CITATION_POLICY.md`
2. `SOURCE_CAPTURE_POLICY.md`
3. `SOURCE_INDEX.md`
4. 対象の手書きノート
5. `HANDWRITTEN_REFERENCE_INDEX.md`
6. `references/REFERENCE_INDEX.md`
7. `SOURCE_GAPS.md`

まず手書きノートから，文献名，著者名，URL，arXiv 番号，DOI，Stacks tag，MathOverflow/Math StackExchange 番号，定理番号，命題番号，節番号，ページ番号，略記，色付き矢印，引き出し線を拾う。
一般検索へ進む前に，スライド，配布資料，板書写真，既存台帳と照合する。

### 主張と参考文献の対応付け

1. `REFERENCE_CITATION_POLICY.md`
2. `CLAIM_REFERENCE_MAP.md`
3. `HANDWRITTEN_REFERENCE_INDEX.md`
4. `SOURCE_INDEX.md`
5. `SESSION_INDEX.md`
6. 対象の手書きノート
7. 対象の板書写真，スライド，配布資料
8. `references/README.md`
9. `references/REFERENCE_INDEX.md`
10. `references/notes/README.md`
11. 必要な参考文献 PDF または公開 URL
12. `NOTATION_CONFLICTS.md`
13. `SOURCE_GAPS.md`

講義中に示された定義，命題，補題，定理，主張，例，注意を一覧化し，対応する参考文献の定理番号，命題番号，節番号，ページ，URL を確認する。
対応は完全一致，記号違いだが内容一致，仮定が一部違う，結論が類似，関連箇所だが対応未確定，未発見に分類する。

### 本文整理

1. `TALK_RECORD_POLICY.md`
2. `SOURCE_CAPTURE_POLICY.md`
3. `REFERENCE_CITATION_POLICY.md`
4. 対象 TeX
5. `SESSION_INDEX.md` の対象行
6. `SOURCE_INDEX.md` の対象資料
7. `HANDWRITTEN_REFERENCE_INDEX.md` の対象行
8. `CLAIM_REFERENCE_MAP.md` の対象行
9. `NOTATION_CONFLICTS.md`
10. `SOURCE_GAPS.md`
11. `TERM_DICTIONARY.md`
12. 未承認語を扱う場合は `TERM_DICTIONARY_CANDIDATES.md`

本文整理では，講義中に記録された内容を読みやすく整える。
証明の不足部分を Codex が補完しない。
参考文献は，引用箇所の特定，講義中の主張との対応確認，記号衝突の確認に使う。

## 4. 作業単位

1. 単発講演では，1 つの話題ブロックを対象にする。
2. 集中講義では，1 つの講義回の中の 1 つの話題ブロックを対象にする。
3. 話題ブロックの粒度は `SESSION_INDEX.md` に従う。
4. 広い範囲を依頼された場合でも，まず話題ブロック一覧を作り，資料確認，参考文献候補抽出，主張対応，本文整理をブロックごとに行う。
5. 話題ブロックをまたぐ記号衝突や参考文献対応は，本文へ混ぜる前に `NOTATION_CONFLICTS.md` または `CLAIM_REFERENCE_MAP.md` に記録する。

## 5. 証明補完禁止

このテンプレートでは，証明補完を行わない。

1. 講義中に記録されていない中間補題を本文へ追加しない。
2. 参考文献に証明が載っていても，講義記録の不足部分を補う目的で本文へ展開しない。
3. 講義中の証明スケッチ，キーワード，図式，引用先は記録として整理してよい。
4. 参考文献は，対応箇所と引用情報を確認するために使う。
5. 証明を補った方がよさそうな場合でも，本文へ直接入れず `REVISION_CANDIDATES.md` または `SOURCE_GAPS.md` に「補完禁止のため未反映」として残す。

## 6. 停止条件

次のどれかに当たる場合は，本文へ曖昧に混ぜない。

1. 手書きノートの文献名，URL，定理番号，ページ番号が判読できない。
2. 文献名は分かるが，対応する定理番号，命題番号，節番号，ページが確認できない。
3. 講義中の主張と参考文献の定理の仮定が一致しているか確認できない。
4. スライド，板書，手書きノート，配布資料で主張の形が食い違う。
5. 参考文献で見つけた主張が，講義で実際に使われたものか判断できない。
6. 参考文献の記号と講義中の記号が衝突し，採用記法を決められない。
7. 用語が `TERM_DICTIONARY.md` の許可待ちまたは使用しない表現に当たる。
8. 証明の不足部分を補完したくなったが，講義中の記録としては残っていない。
9. 講演者が述べたと確定できない内容を，講演者の主張として書くことになりそうである。

停止した場合は，本文変更ではなく，候補，未解決点，確認先を `SOURCE_GAPS.md`，`CLAIM_REFERENCE_MAP.md`，`REVISION_CANDIDATES.md` のいずれかに記録する。

## 7. LaTeX 整形で読む

1. `LATEX_SOURCE_POLICY.md`
2. 対象 TeX
3. 意味が変わる可能性がある場合だけ `TALK_RECORD_POLICY.md`

## 8. 報告形式

作業後は次だけを簡潔に報告する。

1. 対象範囲
2. 使用した資料
3. 変更ファイル
4. 手書きノートから抽出した参考文献候補
5. 講義中の主張と参考文献の対応状況
6. 記号衝突または資料間衝突
7. 実行した確認
8. ビルド結果
9. 未解決点
10. commit するなら推奨 commit 単位
