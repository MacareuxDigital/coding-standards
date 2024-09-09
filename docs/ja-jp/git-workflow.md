# Git Workflow
## リポジトリの命名規則

プロジェクト間の一貫性を保つために、以下のリポジトリの命名規則に従います：

1. リポジトリ名にはハイフンを単語の区切り文字として使用します。例えば、`project-deployer` のように `project_deployer` ではなく。
2. 可能な限り、リポジトリ名を対応するバックログプロジェクト名と一致させます。これにより、明確さを保ち、混乱を避けることができます。

これらのルールに従うことで、一貫性のある整理されたリポジトリの命名規則を確立することができます。


## ブランチのルール

ブランチ | サーバー | コメント
----- | ----- | ----
`master` | 本番環境 | `master` に直接コミットしないでください。`release/x.x.x` から `master` へのPRを作成してください。
`staging` | ステージング環境 | `staging` に直接コミットしないでください。`release/x.x.x` を `staging` にマージして変更をテストしてください。
`develop` | 開発環境 | `fix`/`feature` を `develop` にデプロイして変更をテストしてください。
`release/x.x.x` | 安定したリリースを作成するため | [セマンティックバージョニング](https://semver.org/)を使用してください。前の `release/x.x.x` または `master` から新しいリリースブランチを作成してください。リリース後に [タグ](https://git-scm.com/book/en/v2/Git-Basics-Tagging) を付けることを忘れないでください。
`upgrade/x.x.x` | Concrete CMS のアップグレードに使用 | upgrade/x.x.x をリリースブランチとして扱ってください。修正がレビューを必要としない場合は、直接このブランチにコミットしてください。ただし、コードにレビューが必要な場合は、別のブランチを作成し、このブランチに対してPRを作成してください。
`fix/issue_number` | 修正を行うため | `master` または最新の `release/x.x.x` から新しいブランチを作成してください。`develop` でテストし、次のリリースブランチに対してPRを作成してください。
`hotfix/issue_number` | ホットフィックスを行うため | `master` から新しいブランチを作成してください。プロジェクト固有のgitフローに従ってデプロイしてください。
`feature/issue_number` | 新機能の作業を行うため | `master` または最新の `release/x.x.x` から新しいブランチを作成してください。`develop` でテストし、次のリリースブランチに対してPRを作成してください。
`feature/feature_name` | サブの課題がある場合 | `feature/feature_name` をメインブランチとして使用してください。別々の `issue/issue_number` ブランチからそのブランチに対してPRを作成してください。

詳細は、http://nvie.com/posts/a-successful-git-branching-model/ を参照してください。


## 簡単な手順

- ローカルのプロジェクトディレクトリに移動します `cd YOUR_PROJECT_DIR`
- `master` ブランチにチェックアウトします `git checkout master`
- `master` ブランチから最新の変更を取得します `git pull origin master`
- 実装したい機能のために新しいブランチを作成します `git checkout -b feature/your-new-feature`
- 変更されたファイルを git に追加します `git add .`
- 変更を git にコミットします `git commit -m 'Your commit message'`
- コミットを git にプッシュします。[ブランチ名を指定することを忘れずに。そうしないとすべてのブランチが更新されます] `git push origin feature/your-new-feature`
- `develop` ブランチにチェックアウトします `git checkout develop`
- `develop` ブランチから最新の変更を取得します `git pull origin develop`
- 自分のブランチを `develop` ブランチにマージします `git merge your-new-feature`
- マージコミットを `develop` ブランチにプッシュします。`git push origin develop`
- 変更を `develop` サーバーにデプロイします。
- `develop` サーバーで機能を確認します。
- 問題がなければ、新しいリリースブランチに対してプルリクエストを作成します。リリースが `master` ブランチに対して開けない場合は、そのリリースに対して開けます。
- 問題がある場合は、再度自分のブランチにチェックアウトして上記の手順を行います。既に存在するため、機能ブランチを再作成する必要はありません。


## ヒント

- 適用する前にすべての差分を確認してください
- 関連する変更をコミットしてください
- 頻繁にコミットしてください
- 途中までの作業をコミットしないでください
- コミットする前にテストしてください
- **良いコミットメッセージを書いてください**
- `git push` を避け、`git push origin branch` を使用してください
- 詳細は、https://www.git-tower.com/learn/git/ebook/en/command-line/appendix/best-practices を参照してください。


## プルリクエストのテンプレート
プルリクエストを作成する際には、以下のテンプレートを使用してください。

```
## 説明

変更の概要と、どの問題が修正されたかを含めてください。この変更に必要な依存関係をリストアップしてください。

Fixes # BACKLOG_ISSUE_KEY

## 変更の種類

- [ ] バグ修正（問題を修正する非破壊的な変更）
- [ ] 新機能（機能を追加する非破壊的な変更）
- [ ] 破壊的な変更（既存の機能が正常に動作しなくなる修正または機能）

## どのようにテストされましたか？

変更を検証するために実行したテストについて説明してください。再現できるように手順を提供してください。テスト構成の詳細もリストアップしてください。

- [ ] テスト A
- [ ] テスト B

## チェックリスト：

- [ ] コードがこのプロジェクトのスタイルガイドに従っている
- [ ] 自分自身のコードを自己レビューした
- [ ] コードにコメントを追加し、特に理解しにくい箇所にコメントを付けた
- [ ] ドキュメント/README.md/CHANGELOG.md に対応する変更を行った
- [ ] コードをチェックし、スペルミスを修正した
```


## 参考文献

- https://blog.hartleybrody.com/git-small-teams/ (このヒントが好きです)
- https://stackoverflow.com/questions/24582319/branching-and-merging-best-practices-in-git (ここにはすべての回答に情報がありますが、受け入れられた回答が要約になるかもしれません)
- https://www.git-tower.com/learn/git/ebook/en/command-line/appendix/best-practices (似たようなヒントですが、良いものです)
- https://gist.github.com/pandeiro/1552496 (情報があり、何をすべきか、何をしないかがわかります)
- https://docs.gitlab.com/ee/workflow/gitlab_flow.html (アイデアを得るかもしれません)
- https://www.atlassian.com/git/tutorials/comparing-workflows (詳細について。さまざまなワークフローの非常に良い表現です)
