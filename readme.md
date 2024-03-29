# 簡単な方法：Github Pages 
📖 Docs: https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages

単純なサイト💻（html, css, jsで作成されたもの）を無料で公開するには、Github Pagesを利用するのが簡単です。

## 🪜 手順
1. Githubにリポジトリを作成し、pushする。
2. index.htmlをレポジトリーのルートに配置する。
3. リポジトリーの設定からGithub Pagesを有効にする。Settings -> Pages -> Build and Deployment
4. githubのActionsでビルドが完了すると、URLが表示される: https://USERNAME.github.io/REPOSITORY/

## ⚠️ 注意
- Github Pagesは無料で利用できますが、プライベートリポジトリーの場合は有料です。

## @ Custom Domainを利用する場合
📖 Docs: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
1. ドメインのDNS設定を行う。APEXかsubdomainかによって設定が異なる。subdomainの例：CNAMEレコードを設定する。`CNAME` `subdomain` `USERNAME.github.io.`。待つ（10分ぐらい）。
2. Github repo -> Settings -> Pages -> Custom domainに設定するドメインを入力する。だけ。

> githubがCNAME追加用のcommitを自動で行うので、リポジトリーにCNAMEファイルを作成する必要はありません。

# 🖥️ Virtual Machine (VM)へのデプロイ

## 必要な知識
- basic linux commands
- ssh access
- nginx/apacheの基本的な設定










































# 次は何？
- [ ] docker化：Dockerfileを作成し、コンテナ化する。
- [ ] SSL証明書の設定：Let's Encryptを利用して、httpsを有効にする。
- [ ] CI/CDの設定：Github Actionsを利用して、自動デプロイする。

