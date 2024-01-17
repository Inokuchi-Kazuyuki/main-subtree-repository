# Git Subtree お試し

## リポジトリ準備
```
# main-subtree-repository 作成
# README.md 追加し、cloneする
gh repo create main-sbutree-repository --add-readme --public --clone
```

## Subtree 追加
```
# sub1-repository を Subtree に追加
git subtree add --prefix sub1-repository git@github.com:Inokuchi-Kazuyuki/sub1-repository main --squash
```

## Subtree の更新
```
# main-subtree-repository から sub1-repository のファイルを追加してプッシュ
git add sub1-repository/sub2.txt
git commit -m "XXXXX"
git push -u

# sub1-repository 側へ反映
git subtree push --prefix sub1-repository git@github.com:Inokuchi-Kazuyuki/sub1-repository main

# sub1-repository 側で最新取得
git pull

# sub1-repository 側でファイル更新
git add .
git commit -m "XXXXX"
git push -u

# main-subtree-repository で最新取得
git subtree pull --prefix sub1-repository git@github.com:Inokuchi-Kazuyuki/sub1-repository main --squash
```