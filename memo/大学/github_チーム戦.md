クローン　`git clone hogehoge`
ブランチ切る `git checkout -b NEWブランチ名`
確認　`git branch -a`
add commit して
#`git push origin ブランチ名`！マスターにプッシュすんじゃねーぞ！
→んでプルリクしよう  



ブランチいじってる間に他のとこでマスターに変更があった
→マスターから差分引っ張ってくる
`git merge master`

ぷるリクが通ってmasterにマージされたら
ローカルでマスターに移動
~~`git brabch master`~~
`git checkout ブラ名`
PULL!!
`git fetch`
`git pull`
ローカルの古いブランチは消しとこう
`git branch -d ブラ名`
