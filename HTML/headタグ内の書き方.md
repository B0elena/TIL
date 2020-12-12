## head内の書き方
```html
<head>
①基本的metaタグ
<!-- 文字コードの指定 -->
<meta charset="utf-8">
<!-- IEで常に標準モードで表示させる -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<!-- viewport(レスポンシブ対応) -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- 公開前は検索エンジンにインデックスさせず、他のページの巡回を促す。 -->
<meta name="robots" content="noindex,follow">
<!-- 電話番号の自動リンク化を無効 -->
<meta name="format-detection" content="telephone=no"> 
   
②SEO対策の補助的措置
<!-- サイトのタイトル -->
<title>サイトのタイトルをここに書く</title>
<!-- キーワード -->
<meta name="keywords" content="キーワード1,キーワード2,キーワード3...body内で記載できなかったキーワードがあれば、入れておくと良いでしょう。">
<!-- サイトの説明 -->
<meta name="description" content="ページの要約。130文字以内(目安)">
<!-- 重複するURLを一本化 -->
<link rel="canonical" href="正規化するURL">
  
③SNS対策
<meta property="og:site_name" content="サイト名をここに書きます。">
<meta property="og:title" content="上記titleと同じとする。">
<meta property="og:description" content="上記descriptionと同じとする。">
<meta property="og:type" content="website(トップページ)/article(下位ページ)">
<meta property="og:url" content="サイトのURL">
<meta property="fb:app_id" content="AppID">
<meta name="twitter:card" content="summaryあるいは、summary_large_imageの指定ができます。">
<meta name="twitter:site" content="サイトのURLを記載します。">
</head>
 
④その他の指定
<!-- faviconの指定 -->
<link rel="icon" href="favicon.ico"> 
<!-- 外部のCSSファイル -->
<link rel="styleshee" href="CSSファイルのURL">
<!-- 外部のJsファイル --> 
<script src="JavaScriptファイルのURL"></script>
</head>
```
