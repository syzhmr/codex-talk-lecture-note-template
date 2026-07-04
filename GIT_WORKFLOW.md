# Git 運用メモ

このテンプレートは，Codex との共同編集を Git で管理することを必須とする。
Git は単なるバックアップではなく，Codex の作業監査ログとして使う。
本文整理，方針変更，資料台帳，参考文献対応，修正文候補の変化を commit 単位で追えるようにする。

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

1. 方針変更，本文整理，LaTeX 整形，資料台帳更新，参考文献対応，修正文候補を混ぜない。
2. TeX 本文を変更した場合は，話題ブロックごとにビルドする。
3. ユーザーが作った未コミット変更は戻さない。
4. 手書きノート，板書写真，スライド，配布資料，録音，文字起こし，参考文献 PDF，抽出画像は原則として Git に入れない。
5. 例外的に PDF や画像を Git 管理する場合は，`PROJECT_PROFILE.md` と `references/REFERENCE_INDEX.md` に理由，権利，容量，分割方針を記録する。
6. LaTeX 補助ファイル，ビルドキャッシュ，一時作業ディレクトリは Git に入れない。`*:Zone.Identifier` は見つけ次第削除し，Git に入れない。

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
git add SOURCE_INDEX.md SESSION_INDEX.md HANDWRITTEN_REFERENCE_INDEX.md SOURCE_GAPS.md
git commit -m "Record lecture source inventory"
```

参考文献対応:

```sh
git add HANDWRITTEN_REFERENCE_INDEX.md CLAIM_REFERENCE_MAP.md NOTATION_CONFLICTS.md SOURCE_GAPS.md references/REFERENCE_INDEX.md references/notes/
git commit -m "Map lecture claims to references"
```

本文整理:

```sh
git add final/ CLAIM_REFERENCE_MAP.md NOTATION_CONFLICTS.md SOURCE_GAPS.md REVISION_CANDIDATES.md
git commit -m "Organize talk record block T1-01"
```

方針変更:

```sh
git add README.md PROJECT_PROFILE.md WORKFLOW_STEPS.md TALK_RECORD_POLICY.md SOURCE_CAPTURE_POLICY.md REFERENCE_CITATION_POLICY.md LATEX_SOURCE_POLICY.md GIT_WORKFLOW.md SOURCE_INDEX.md SESSION_INDEX.md
git commit -m "Update talk lecture workflow"
```

PDF や画像を例外的に Git 管理する場合:

```sh
git add PROJECT_PROFILE.md references/REFERENCE_INDEX.md [approved-file]
git commit -m "Add approved local lecture asset"
```

## 大容量資料

GitHub は通常 Git blob で 100MB 超のファイルを拒否する。
Git LFS を使わない運用では，次の順で対応する。

1. その資料を Git 管理する必要が本当にあるか確認する。
2. 権利上共有できるか確認する。
3. 共有する必要がある場合は，講義回，ページ，画像範囲など意味のある単位で分割し，各ファイルを 100MB 未満にする。
4. 元資料は `.gitignore` 対象のローカル保管資料にする。
5. 分割版の範囲，ページ数，元資料との関係を `references/notes/` または該当資料ディレクトリの README に記録する。
6. すでに未 push commit に 100MB 超資料を入れた場合は，後続 commit で削除しても push は通らない。未 push commit を amend し，巨大 blob を履歴から外す。

## commit 実行条件

1. ユーザーが明示的に commit を依頼した。
2. `git diff --check` が通っている。
3. TeX 本文変更ならビルド結果を確認済みである。
4. commit 対象が一つの意味単位にまとまっている。
5. `git var GIT_AUTHOR_IDENT` と `git var GIT_COMMITTER_IDENT` が通っている。
