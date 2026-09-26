# Animecia

**Animecia（アニメシア）** は、「次に見るアニメを見つける」をコンセプトにした、アニメ情報・検索・レビュー・お気に入り管理などを提供するWebサービスです。

## サービス

* **サイト名:** Animecia
* **コンセプト:** 次に見るアニメを見つける
* **公開サイト:** https://media-mania.github.io/Animecia/
* **リポジトリ:** Just-an-Anime-Review.github.io

## 主な機能

### アニメ情報

アニメ作品について、以下の情報を掲載・管理します。

* 作品タイトル
* ローマ字タイトル
* 英語タイトル
* 日本語タイトル
* あらすじ
* キービジュアル
* バナー画像
* 放送開始日・終了日
* 話数
* 放送時間
* ステータス
* 形式
* 放送クール
* 放送年
* 原作
* 評価
* 人気度
* お気に入り数
* 公式サイト

### アニメ検索・絞り込み

以下の条件からアニメを探すことができます。

* タイトル
* 年
* クール
* 放送ステータス
* 形式
* 評価
* 人気度
* 新着
* タイトル順

今後、ジャンル・スタジオなどの条件も拡張予定です。

### ユーザー機能

アカウントを作成することで、以下の機能を利用できます。

* 新規登録
* ログイン
* ログアウト
* プロフィール
* お気に入り登録
* 視聴ステータス管理
* 視聴進捗管理
* ユーザー評価
* レビュー投稿
* レビューへのいいね

### 視聴ステータス

作品ごとに以下の状態を管理できます。

* 視聴中
* 視聴完了
* 視聴予定
* 中断
* 一時停止

### レビュー

ユーザーはアニメ作品に対してレビューを投稿できます。

* レビュータイトル
* レビュー本文
* 評価（1～10）
* ネタバレ設定
* いいね数
* 投稿日

### おすすめ作品

管理者が選択したおすすめ作品をトップページに掲載できます。

### 広告

広告管理機能を利用して、サイト内に広告を掲載できます。

* 企業名
* 広告タイトル
* 説明
* 画像
* リンク
* 公開・非公開設定

## 技術構成

Animeciaは、主に以下の技術を使用しています。

### フロントエンド

* HTML
* CSS
* JavaScript
* GitHub Pages

### データベース・認証

* Supabase
* PostgreSQL
* Supabase Auth
* Supabase Storage

### アニメ情報

外部アニメデータAPIから取得した情報をSupabaseへ保存し、Animeciaから利用する構成を予定しています。

```text
外部アニメAPI
      ↓
Supabase Edge Functions
      ↓
Supabase PostgreSQL
      ↓
Animecia
      ↓
GitHub Pages
```

定期的なデータ更新にはSupabase Cronの利用を予定しています。

## データベース

主要なテーブルは以下のとおりです。

### アニメ関連

* `anime`
* `genres`
* `anime_genres`
* `studios`
* `anime_studios`
* `characters`
* `anime_characters`
* `voice_actors`
* `character_voice_actors`
* `staff`
* `anime_staff`
* `anime_relations`

### ユーザー関連

* `profiles`
* `favorites`
* `user_anime_status`
* `user_ratings`
* `reviews`
* `review_likes`

### サイト管理

* `recommended_anime`
* `advertisements`

## ディレクトリ構成

```text
Just-an-Anime-Review.github.io/
│
├── index.html
├── anime.html
├── anime-detail.html
├── admin.html
├── admin-dashboard.html
├── terms.html
├── privacy.html
│
├── style.css
│
├── README.md
│
└── その他の画像・設定ファイルなど
```

## Supabase

AnimeciaではSupabaseをバックエンドとして利用しています。

主な用途：

* PostgreSQLデータベース
* ユーザー認証
* ユーザープロフィール
* お気に入り
* 視聴ステータス
* 評価
* レビュー
* レビューへのいいね
* 広告画像の保存

### セキュリティ

フロントエンドにはSupabaseの**Publishable Key**を使用します。

**Service Role Keyなどの秘密鍵をHTMLやJavaScriptに記述しないでください。**

管理者向けのデータ更新処理については、SupabaseのRLS（Row Level Security）やEdge Functionsなどを利用して権限を管理します。

## SEO

Animeciaでは検索エンジンからアニメ作品を発見してもらうため、以下のSEO対策を行います。

* title
* meta description
* canonical URL
* OGP
* JSON-LD
* sitemap
* robots.txt
* 内部リンク
* アニメ作品ごとの詳細ページ

## 管理画面

管理者向けに以下の管理機能を提供します。

### アニメ管理

* アニメの追加
* アニメ情報の編集
* アニメ情報の削除
* 検索
* ジャンル管理

### おすすめ作品管理

* おすすめ作品の追加
* 表示期間設定
* 表示順設定
* 公開・非公開設定

### レビュー管理

* レビュー一覧
* レビュー検索
* レビュー内容確認
* レビュー削除

### 広告管理

* 広告追加
* 広告編集
* 広告削除
* 広告画像アップロード
* 公開・非公開設定

## 開発方針

Animeciaは、まず無料で利用できるサービス・プランを中心に開発します。

初期段階では、

* GitHub Pages
* Supabase Free Plan
* 無料で利用可能な外部API

などを活用し、できるだけ初期費用を抑えて開発します。

ただし、各API・画像・サービスの利用規約や商用利用条件については、実際の公開・収益化前に確認します。

## 今後追加予定の機能

* ジャンル別ランキング
* スタジオ別検索
* キャラクター検索
* 声優検索
* スタッフ検索
* 関連作品表示
* 配信サービス情報
* より高度な検索
* ユーザーランキング
* レビューランキング
* おすすめアルゴリズム
* アニメ視聴履歴
* マイページの強化
* 通知機能
* SEOの強化
* アフィリエイト連携

## 目標

Animeciaの目標は、単なるアニメデータベースではなく、

> **「次に見るアニメが見つかる場所」**

になることです。

作品情報を調べるだけでなく、評価・レビュー・ジャンル・関連作品・人気度などを組み合わせて、ユーザーが自分に合った作品を探せるサービスを目指します。

## ライセンス・権利について

Animeciaで利用するアニメ作品の情報、画像、外部APIなどについては、それぞれの提供元の利用規約・ライセンス・著作権等に従って利用します。

外部サービスから取得したデータについては、各サービスの利用条件を確認した上で利用してください。

## 関連サイト

* Animecia: https://media-mania.github.io/Animecia/
* 季節アニメMAKI: https://kisetsu-anime.com/
* MyAnimeList: https://myanimelist.net/
* Supabase: https://supabase.com/
* GitHub Pages: https://pages.github.com/

---

© 2026 Animecia
