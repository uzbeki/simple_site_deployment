# 簡単な方法：Github Pages 
📖 Docs: https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages

単純なサイト💻（`HTML`, `CSS`, `JavaScript`で作成されたもの）を無料で公開するには、Github Pagesを利用するのが簡単です。

## 🪜 手順
1. Githubにリポジトリを作成し、pushする。
2. `index.html`をレポジトリーのルートに配置する。
3. リポジトリーの設定からGithub Pagesを有効にする。**Settings -> Pages -> Build and Deployment**
4. githubのActionsでビルドが完了すると、URLが表示される: https://USERNAME.github.io/REPOSITORY/

## ⚠️ 注意
- Github Pagesは無料で利用できますが、プライベートリポジトリーの場合は**有料**です。

## @ Custom Domainを利用する場合
📖 Docs: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
1. ドメインのDNS設定を行う。APEXかsubdomainかによって設定が異なる。subdomainの例：CNAMEレコードを設定する。`CNAME` `subdomain` `USERNAME.github.io.`。待つ（10分ぐらい）。
2. `Github repo -> Settings -> Pages -> Custom domain`に設定するドメインを入力する。だけ。

> githubがCNAME追加用のcommitを自動で行うので、リポジトリーにCNAMEファイルを作成する必要はありません。

# 🖥️ Virtual Machine (VM)へのデプロイ
Ubuntu Server 22.04 LTSを利用して、Virtual Machineにデプロイする方法を紹介します。クリーンインストールの状態です。

## 必要な知識
- basic linux commands
- ssh access
- nginx/apacheの基本的な設定

## 🪜 手順
1. VMにsshで接続する。`ssh -t ubuntu@ip_address`
2. `sudo apt update && sudo apt upgrade -y`でアップデートを行う。

    VMのIPアドレスにブラウザーでアクセスすると、最初は何も表示されません。Webサーバーが必要です。人気のあるのは２つです：`nginx`と`apache`です。今回は`nginx`を利用します。Docs: [https://nginx.org/en/docs/](https://nginx.org/en/docs/)

3. `sudo apt install nginx -y`でnginxをインストールする。
    インストール後、もう一回ブラウザーでipアドレスにアクセスすると、nginxのデフォルトページが表示されます。もう動いています。
    nginxはどこからこのデフォルトページを取得しているのか？`/var/www/html`に配置されています。次は、このディレクトリーに自分のファイルを配置する方法です。
4. `cd /var/www/html`でディレクトリーに移動する。
5. `sudo nano index.html`でファイルを作成する。`Hello, World!`を入力し、保存する。
    ブラウザーでipアドレスにアクセスすると、`Hello, World!`が表示されます。
6. index.htmlを削除し、自分のレポジトリーからファイルを取得する方法を紹介します。
    - `sudo rm index.html`でファイルを削除する。
    - `git`はすでにインストールされているから、`git clone repository_url`でファイルを取得する。
    clone後、`ls`でファイルがあることを確認する。ipアドレスにアクセスすると、ファイルが表示されます。🥳

## @ Custom Domainを利用する場合
1. ドメインのDNS設定を行う。例：Aレコードを設定する。`A` `@` `ip_address`。待つ（10分ぐらい）。
    - DNSが変わったことを確認するために、`dig domain_name`で確認する。
2. `sudo nano /etc/nginx/sites-available/default`で設定ファイルを開く。
3. `server_name _;`を`server_name domain_name;`に変更する。
4. `sudo systemctl restart nginx`でnginxを再起動する。
5. ブラウザーでドメインにアクセスすると、ファイルが表示されます。👏




































# 次は何？
- [ ] docker化：Dockerfileを作成し、コンテナ化する。
- [ ] SSL証明書の設定：Let's Encryptを利用して、httpsを有効にする。
- [ ] CI/CDの設定：Github Actionsを利用して、自動デプロイする。

