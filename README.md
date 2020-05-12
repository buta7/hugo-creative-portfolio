# README

## セットアップ

サイト作成

    $ hugo new site hugo-creative-portfolio
        
レポジトリ初期化

    $ cd hugo-creative-portfolio
    $ git init
    $ echo '*.bak' >> .gitignore
    $ echo '*~' >> .gitignore
    $ echo '*.orig' >> .gitignore
    $ echo 'public' >> .gitignore
    
テーマ設定
    
    $ cd themes 
    $ git submodule add https://github.com/kishaningithub/hugo-creative-portfolio-theme.git

サイト設定

    $ cd hugo-creative-portfolio
    $ cp -pr ./themes/hugo-theme-dream/exampleSite/* .

config.toml

```
baseURL = "http://higebobo.github.io/hugo-creative-portfolio/"
title = "Hugo Creative portfolio"
theme = "hugo-creative-portfolio-theme"
languageCode = "ja"
publishDir = "docs"
```

archetypesの設定

archetypes/portfolio.md

```
+++
image = "img/portfolio/gravity-paper.jpg"
showonlyimage = true
date = {{ .Date }}
title = "{{ replace .Name "-" " " | title }}"
draft = true
weight = 10
+++
```

Githubレポジトリ作成後

    $ git remote add origin git@github.com:higebobo/hugo-creative-portfolio.git
    $ git add -A
    $ git commit -m 'init'
    $ git push -u origin master

## 使い方

### 投稿

新規ポートフォリオ

    $ hugo new portfolio/work12.md
    content/portfolio/work12.md created
    
編集

    $ vi content/portfolio/work12.md

下書きモード解除

    $ vi content/posts/2020/05/helloworld.md
    ...
    draft: false
    ...

固定ページの作成(architypeのabout.mdを使う)

    $ hugo new about/_index.md
    ...
    
上記ファイル構成を元にconfig.tomlのメニューを設定

    [[menu.main]]
      name = "Blog"
      url = "posts"
      weight = 1
    
    [[menu.main]]
      name = "Tags"
      url = "tags"
      weight = 2
    
    [[menu.main]]
      name = "About"
      url = "page/about/"
      weight = 3

プレビュー(http://localhost:1313)

    $ make run

## Github連携

config.tomlに以下の設定

    baseURL = "https://higebobo.github.com/blog-hugo/"
    publishDir = "docs"

公開(githubにプッシュ)

    $ make deploy

## Link

* [Hugo Creative Portfolio Theme \| Hugo Themes](https://themes.gohugo.io/hugo-creative-portfolio-theme/)
