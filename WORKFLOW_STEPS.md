# 再現可能作業手順

このファイルを Codex 作業の入口にする。
目的は，毎回読む Markdown を減らしつつ，本文の品質判定を軽くしないことである。

## 0. 作業開始

1. `git status --short --branch` を確認する。
2. ユーザーの依頼を次の型に分ける。
   - 方針変更
   - 資料台帳更新
   - 手書きノート確認
   - 参考文献確認
   - 本文整理
   - LaTeX 整形
   - 用語・記号確認
   - Git 操作
3. 型に応じて読むファイルを絞る。
4. 未コミット変更がある場合は，変更元と作業範囲を確認し，無関係な変更を壊さない。
5. ユーザーが `sources/` または `references/` に入れた資料は，未登録なら `WORK_LEDGER.md` または `references/REFERENCE_INDEX.md` に登録してから使う。

## 1. 常に読む

1. `WORKFLOW_STEPS.md`
2. `PROJECT_PROFILE.md`
3. `GIT_WORKFLOW.md`

## 2. 作業型ごとの読むファイル

| 作業型 | 読むファイル |
| --- | --- |
| 方針変更 | `README.md`, `PROJECT_PROFILE.md`, `NOTE_POLICY.md`, `WORKFLOW_STEPS.md`, `WORK_LEDGER.md`, `TERM_DICTIONARY.md`, `LATEX_SOURCE_POLICY.md`, `GIT_WORKFLOW.md`, `references/README.md` |
| 資料台帳更新 | `PROJECT_PROFILE.md`, `WORK_LEDGER.md`, `sources/README.md`, `references/README.md`, `references/REFERENCE_INDEX.md` |
| 手書きノート確認 | `NOTE_POLICY.md`, `WORK_LEDGER.md`, 対象の手書きノートまたは単ページ画像 |
| 参考文献確認 | `NOTE_POLICY.md`, `WORK_LEDGER.md`, `references/README.md`, `references/REFERENCE_INDEX.md`, 必要な `references/notes/` の個別メモ |
| 本文整理 | `NOTE_POLICY.md`, `WORK_LEDGER.md`, `TERM_DICTIONARY.md`, 対象 TeX |
| LaTeX 整形 | `LATEX_SOURCE_POLICY.md`, 対象 TeX。意味変更の可能性がある場合は `NOTE_POLICY.md` も読む。 |
| 用語・記号確認 | `TERM_DICTIONARY.md`, `NOTE_POLICY.md`, `WORK_LEDGER.md` |
| Git 操作 | `GIT_WORKFLOW.md` |

## 3. 本文整理の手順

1. 対象を，完成済み目次の最小単位または `WORK_LEDGER.md` の話題ブロックに固定する。
2. 対象ページ，対象資料，反映先 TeX，ロック済み範囲，未解決点を短く列挙する。
3. 手書きノートを OCR にかけず，1 ページずつ確認する。contact sheet だけを根拠にしない。
4. 見出し，小見出し，定義・定理・命題，本文，式，図式，矢印，欄外メモ，レポート問題，証明または sketch を抽出する。
5. 参考文献候補，記号衝突，判読不能箇所を `WORK_LEDGER.md` に分ける。
6. 本文へ反映する。手書きノートにない証明補完や接続文は入れない。
7. 作業用表現が本文へ残っていないか確認する。
8. 本文を修正した場合は原則としてビルドする。
9. `WORK_LEDGER.md` の状態を更新し，完成扱いにできない理由を残す。

## 4. 完成判定

完成扱いにするには，次を満たす。

1. 対象範囲の手書きノートをページ単位で確認している。
2. 本文が手書きノートより薄くなっていない。
3. 見出し，式，図式，欄外注，レポート問題の扱いが決まっている。
4. 参考文献対応，記号差，判読不能箇所が `WORK_LEDGER.md` または `references/notes/` に分離されている。
5. 本文に作業用表現が残っていない。
6. ロック済み範囲を勝手に変更していない。
7. 必要なビルドまたは検査を実行している。

## 5. 停止条件

次の場合は本文へ推測で入れず，`WORK_LEDGER.md` に残す。

- 手書きノートが判読できない。
- 参考文献との仮定・対象・結論の差が解消できない。
- 記号衝突の採用記法を決められない。
- レポート問題や欄外注の対象範囲が画像上で確定できない。
- 証明補完が必要に見えるが，手書きノートに根拠がない。
- ユーザー確認でロック済みの範囲を変更する必要がある。

## 6. 報告

報告では次を短く書く。

1. 対象範囲。
2. 確認した資料。
3. 本文へ反映した内容。
4. 更新した台帳。
5. 残した未解決点。
6. 実行した検査またはビルド。
