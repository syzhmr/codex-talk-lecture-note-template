# Git 運用メモ

このテンプレートは，Codex との共同編集を Git で管理することを必須とする。
Git は単なるバックアップではなく，Codex の作業監査ログとして使う。
本文整理，方針変更，資料台帳，参考文献対応の変化を commit 単位で追えるようにする。

## 関連 URL

- テンプレート: <https://github.com/syzhmr/codex-talk-lecture-note-template>
- 関連テンプレート: <https://github.com/syzhmr/codex-study-note-template>
- 推奨 devcontainer: <https://github.com/syzhmr/LaTeX/tree/main/.devcontainer>

## 作業開始

1. `WORKFLOW_STEPS.md` で作業型を決める。
2. `git status --short --branch` を確認する。
3. 未コミット変更がある場合は，自分の作業範囲と衝突しないか確認する。
4. `git var GIT_AUTHOR_IDENT` と `git var GIT_COMMITTER_IDENT` で identity を確認する。
5. ローカルの `user.name` / `user.email` は原則として置かず，global 設定を使う。プロジェクト固有の理由がある場合だけ local 設定を使い，理由を残す。

## 作業中

1. 方針変更，本文整理，LaTeX 整形，資料台帳更新，参考文献対応を混ぜない。
2. TeX 本文を変更した場合は，話題ブロックごとにビルドする。
3. ユーザーが作った未コミット変更は戻さない。
4. 手書きノート，板書写真，スライド，配布資料，録音，文字起こし，参考文献 PDF，参考文献 PDF から作った検索用テキスト，抽出画像，作業画像は，大学や別端末で同期して作業できるように原則 Git で追跡する。
5. GitHub の 100MB 制限，公開範囲，権利上の問題がある資料だけを個別例外として除外し，`PROJECT_PROFILE.md`，`WORK_LEDGER.md`，`references/REFERENCE_INDEX.md` に理由，代替ファイル，容量，分割方針，保管場所を記録する。
6. `public/` 以下へ置く資料は，外部公開してよい内容か個別に確認する。
7. `work/` の画像抽出，文字起こし，確認用メモなど，資料復元や本文確認に必要な作業資料は Git で追跡する。OCR は参考文献 PDF の検索補助に限り，生成物は `references/text/` に置く。
8. LaTeX 補助ファイル，ビルドキャッシュ，再生成だけを目的とした一時キャッシュは Git に入れない。ただし `main_final.log` はビルド確認用，`main_final.synctex.gz` は SyncTeX 用として保持し，削除しない。cleanup 後に消えていないか確認し，消えた場合は再ビルドで復元する。
9. LaTeX 補助生成物を ignore する場合も，`*.log` と `*.synctex.gz` は入れない。`*:Zone.Identifier` や `.DS_Store` は見つけ次第削除し，Git に入れない。

## 作業後

1. `git diff` を確認する。
2. `git diff --check` を実行する。
3. TeX 本文を変更した場合はビルド結果を確認する。
4. commit する単位を決める。
5. ユーザーから commit 指示がある場合だけ commit する。
6. commit した場合は `git status --short --branch` を再確認する。

## commit 単位

資料台帳更新:

```sh
git add WORK_LEDGER.md
git commit -m "Record lecture source inventory"
```

参考文献対応:

```sh
git add WORK_LEDGER.md references/REFERENCE_INDEX.md references/notes/
git commit -m "Map lecture claims to references"
```

Codex 提案参考文献:

```sh
git add WORK_LEDGER.md references/REFERENCE_INDEX.md references/notes/
git commit -m "Record Codex proposed reference candidates"
```

本文整理:

```sh
git add final/ main_final.log main_final.pdf main_final.synctex.gz WORK_LEDGER.md
git commit -m "Organize talk record block T1-01"
```

方針変更:

```sh
git add README.md PROJECT_PROFILE.md WORKFLOW_STEPS.md NOTE_POLICY.md WORK_LEDGER.md LATEX_SOURCE_POLICY.md GIT_WORKFLOW.md TERM_DICTIONARY.md sources/README.md references/README.md references/REFERENCE_INDEX.md
git commit -m "Update talk lecture workflow"
```

PDF や画像を Git 管理に追加する場合:

```sh
git add PROJECT_PROFILE.md WORK_LEDGER.md references/REFERENCE_INDEX.md [asset-file]
git commit -m "Add lecture asset"
```

## 大容量資料

GitHub は通常 Git blob で 100MB 超のファイルを拒否する。
Git LFS を使わない運用では，次の順で対応する。

1. その資料をそのまま追跡できる容量か確認する。
2. 権利上共有できるか確認する。
3. 100MB 未満で共有可能な資料は，台帳登録した上で通常どおり追跡する。
4. 100MB 超の元資料は，講義回，ページ，画像範囲など意味のある単位で分割し，各ファイルを 100MB 未満にする。
5. 100MB 超の元資料は `.gitignore` または `.git/info/exclude` に明示して除外し，分割版を追跡する。
6. 分割版の範囲，ページ数，元資料との関係を `WORK_LEDGER.md`，`references/REFERENCE_INDEX.md`，`references/notes/`，または該当資料ディレクトリの README に記録する。
7. すでに未 push commit に 100MB 超資料を入れた場合は，後続 commit で削除しても push は通らない。未 push commit を amend し，巨大 blob を履歴から外す。

## commit 実行条件

1. ユーザーが明示的に commit を依頼した。
2. `git diff --check` が通っている。
3. TeX 本文変更ならビルド結果を確認済みである。
4. commit 対象が一つの意味単位にまとまっている。
5. `git var GIT_AUTHOR_IDENT` と `git var GIT_COMMITTER_IDENT` が通っている。
