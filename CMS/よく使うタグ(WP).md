## 【インクルードタグ】 header.phpのようなテンプレートファイルを読み込みたい時に使うタグ
|意味|タグ|
|-|-|
|header.phpの読み込み|```<?php get_header(); ?>```|
|footer.phpの読み込み|```<?php get_footer(); ?>```|
|sidebar.phpの読み込み|```<?php get_sidebar(); ?>```|
|独自で作ったたファイルの読み込み|```<?php get_template_part(); ?>```|
|検索フォームの表示|```<?php get_search_form(); ?>```|
|コメントテンプレーのを読み込み|```<?php comments_template(); ?>```|

## 【テンプレートタグ】 コンテンツをサイトに表示するためのタグ
- 基本情報の出力

|意味|タグ|
|-|-|
|管理画面「一般設定」で設定したサイトのタイトルを出力|```<?php bloginfo( 'name' ); ?>```|
|管理画面「一般設定」で設定したサイトのキャッチフレーズを出力|```<?php bloginfo( 'description' ); ?>```|
|「UTF-8」が出力される|```<?php bloginfo( 'charset' ); ?>```|
|一般設定のサイトの言語を出力|```<?php bloginfo( 'language' ); ?>```|
|現在のブログのホームURLを出力|```<?php echo home_url(); ?>```|
|現状のテーマのスタイルシートのURI を取得し、表示|```<?php echo get_stylesheet_uri(); ?>```|
|親テーマのディレクトリのURI を取得し、表示|```<?php echo get_template_directory_uri(); ?>```|
|子テーマのディレクトリのURI を取得し、表示|```<?php echo get_stylesheet_directory_uri(); ?>```|
|/head タグ直前で使用|```<?php wp_head(); ?>```|
|/body タグ直前で使用|```<?php wp_footer(); ?>```|
 
## 【classの追加】
|意味|タグ|
|-|-|
|bodyにclass名を追加|```<?php body_class(); ?>```|
|投稿IDを任意の場所に出力|```<?php post_class(); ?>```|

## 【投稿関連】
|意味|タグ|
|-|-|
|現在の投稿のタイトルを表示|```<?php the_title(); ?>```|
|現在の投稿の本文を出力|```<?php the_content(); ?>```|
|現在の投稿の抜粋を表示|```<?php the_excerpt(); ?>```|
|投稿編集画面で設定されたアイキャッチ画像|```<?php the_post_thumbnail(); ?>```|
|現在の記事が属するカテゴリーへのリンクを表示 ※必ずループの中で使う|```<?php the_category(); ?>```|
|現在の記事に付けられたタグを表示 ※必ずループの中で使う|```<?php the_tags(); ?>```|
|現在の投稿の公開時刻日時を表示|```<?php the_time(); ?>```|
|年月日を表示する|```<?php the_date(); ?>```|
|取得したデータを、echoで表示|```<?php echo get_the_date(); ?>```|
|投稿のパーマリンクのURLを表示 ※必ずループの中で使う|```<?php the_permalink(); ?>```|
|投稿作成者のブログ上の表示名を表示|```<?php the_author(); ?>```|
|現在の投稿のIDを表示。 ※必ずループの中で使う|```<?php the_ID(); ?>```|

## 【ナビゲーション】
▼現在の投稿より新しい投稿へのリンクを表示 ※必ずループの中で使う

 <?php next_post_link(); ?>
▼現在の投稿よりひとつ前の投稿へのリンクを表示 ※必ずループの中で使う必要
<?php previous_post_link(); ?>
▼現在のクエリ内で、投稿の次のセットへのリンクを表示 <?php next_posts_link(); ?>
▼現在のクエリ内で、投稿の一つ前のセットへのリンクを表示 <?php previous_posts_link(); ?>
▼管理画面>外観 >メニューで作成したナビゲーションメニューを表示 <?php wp_nav_menu(); ?>
【Author】
▼投稿作成者のブログ上の表示名を表示 <?php the_author(); ?>
▼投稿作成者のウェブサイトへのリンク <?php the_author_link(); ?>
▼投稿作成者の表示名とともに著者ページへのリンクを表示 <?php the_author_posts_link(); ?>
▼ユーザーが持つメタデータから好きなものを表示

<?php the_author_meta(); ?>
 ▼投稿の作成者が公開した投稿の総数を表示 <?php the_author_posts(); ?>
【条件分岐】
■主要な条件分岐タグ
▼メインの投稿ページかを判定 is_home()
▼フロントページかを判定 is_front_page()
▼投稿タイプを判定 is_singular()
▼個別の投稿ページかを判定 is_single()
▼固定ページかを判定 is_page()
▼ページテンプレートが使われているかを判定 is_page_template()

■アーカイブページの条件分岐タグ
 ▼各アーカイブページが表示されているかを判定 is_archive()
▼ページが $category カテゴリーと関連付けられているかを判定 is_category()
▼タグのアーカイブページが表示されているかを判定 is_tag()
▼タクソノミーのアーカイブページが表示されているかを判定 is_tax()
▼タクソノミーのアーカイブページが表示されているかを判定 is_tax()
▼作成者のアーカイブページが表示されているかを判定 is_author()
▼日付に関連するアーカイブページが表示されているかを判定 is_date()
■その他の条件分岐タグ
▼404 Not Found エラーページが表示されているかを判定 is_404()

 ▼表示中のページが複数のページにまたがるかを判定 is_paged()
▼ダッシュボードまたは管理パネルが表示されているかを判定 is_admin()
▼ユーザーがログインしているかを判定 is_user_logged_in()
【ループ(メインループとサブループ)】
// ループ開始
<?php if ( have_posts() ) : ?>
<?php while ( have_posts() ) : the_post(); ?> // 投稿内容を出力
...
<?php endwhile; else : ?>
// 投稿がない場合の表示を処理
...
<?php endif; ?>
// サブループの準備(例) <?php $args = array(
'category_name' => 'music',
'order' => 'DESC', ); ?>
<?php $the_query = new WP_Query( $args ); ?>

// サブループ開始
<?php if ( $the_query->have_posts() ) : ?>
<?php while ( $the_query->have_posts() ) : $the_query->the_post(); ?> // 投稿内容を出力
...
<?php endwhile; ?> // サブループ終了
<?php wp_reset_postdata(); ?> //クエリリセット(重要)
<?php else : ?>
// 投稿がない場合の表示を処理
...
<?php endif; ?>
