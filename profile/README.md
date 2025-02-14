# 文章新規作成時のやり方

手順をミスっている場合があったり、通常と異なる使い方を推奨したいので、書いておきます

Docker for Windowsを使用する前提ですが、一部の手順は他のOSでも同じです

## docker imageを更新する

コマンドラインで`docker pull ghcr.io/being24/latex-docker:latest`を実行するか、Docker DesktopのGUIからPullを実行してください

@[osf](9q578)

## gitの改行コードの設定を変更する(１回だけ)

gitの改行コードの自動変更設定を変更する必要があります。
`git config --global core.autocrlf false`を実行してください

## ローカルの環境を整理する(必要なら)

docker imageは大きいので不要なものを削除したほうがいいですが、操作手順が複雑なので難しいときは無視してください。

1. まず、削除したいimageを使用しているコンテナを削除する
    1. `docker ps -a`でコンテナの一覧を表示する
    2. `docker rm <コンテナID>`でコンテナを削除する
2. 削除したいimageを削除する
    1. `docker images`でimageの一覧を表示する
    2. `docker rmi <imageID>`でimageを削除する

最終手段として、
`docker system prune`を実行すると、全ての不要なものを削除できます
ただし、これで消したくなかったものが消えても責任は取れません

## Templateリポジトリを使用して、新しいリポジトリを作成する

1. [Templateリポジトリ](https://github.com/being24/latex-template-ja)を開く
2. 右上の`Use this template`をクリック、`Create a new repository`をクリック
@[osf](juwqd)
3. Ownerを`kawamlab`に変更し、Repository nameを以下の規則で設定する
    1. 名前の構成は学会の場合は`学会名_内容_著者`、学内発表は`学年_年度識別_著者`とする
    2. 学内発表の年度の識別は、中間発表はQ(qualify)、最終発表はF(final)とする
    3. 例: `SI2022_LRF_yamada`、`B4_2022Q_tanaka`
4. Descriptionに詳細を書く
@[osf](psr7n)
5. Privateを選択し、Create repositoryをクリック
6. 作成したリポジトリをcloneし、VSCodeで開く
7. 執筆する
8. .gitignoreに`!main.pdf`を追記する
