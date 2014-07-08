twitter-bootstrap-rails + simple_form プロジェクト作成手順
==========================================================

この手順は rails に twitter-bootstrap-rails と simple_form を適用する手順です。
各バージョンは以下を使用しています。

- Rails 4.1.1
- twitter-bootstrap-rails 3.1.1  (bootstrap3 branch)
- simple_form 3.1.0.rc1



1. rails インストール

 ```````````````````
 $ gem install rails
 ```````````````````

2. rails プロジェクト作成

 ````````````````````````````````````````
 $ rails new bootstrap3-simpleform-sample
 ````````````````````````````````````````

3. bootstrap-rails と simple_form をインストール

 以下を Gemfile に追加して bundle を実行する
 ```````````````````````````````````````````````````````````````````````````````````````
 gem "therubyracer"
 gem "less-rails" #Sprockets (what Rails 3.1 uses for its asset pipeline) supports LESS
 gem 'twitter-bootstrap-rails', :git => 'git://github.com/seyhunak/twitter-bootstrap-rails.git', :branch => "bootstrap3"
 gem 'simple_form', '~> 3.1.0.rc1', github: 'plataformatec/simple_form'
 ```````````````````````````````````````````````````````````````````````````````````````


4. Bootstrap のジェネレータを実行

 `````````````````````````````````````
 rails generate bootstrap:install less
 `````````````````````````````````````


5. application レイアウトに bootstrap を適用

 ````````````````````````````````````
 rails g bootstrap:layout application
 ````````````````````````````````````


6. scaffold でサンプルモデルを作成し、DBマイグレートを実行

 ```````````````````````````````````````````````````
 rails g scaffold Post title:string description:text
 rake db:migrate
 ```````````````````````````````````````````````````


7. simple_form のインストール

 ``````````````````````````````````````````````
 rails generate simple_form:install --bootstrap
 ``````````````````````````````````````````````


8. 既存の view に bootstrap + simple_form を適用する

 ``````````````````````````````
 rails g bootstrap:themed Posts
 ``````````````````````````````


9. A タグのボタンテキスト色が変なので、スタイルシートを追加する

  app/assets/stylesheets/application.css を編集で以下を追加

 ```````````````````````````````````````````
 a.btn-primary, a.btn-danger, a.btn-success,
 a.btn-info, a.btn-warning, a.btn-danger {
   color: #fff;
 }
 ```````````````````````````````````````````

10. 完了
