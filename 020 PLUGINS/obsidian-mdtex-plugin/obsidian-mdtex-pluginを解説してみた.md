## レポジトリ

[GitHub - Mekann2904/obsidian-mdtex-plugin: obsidian plugin](https://github.com/Mekann2904/obsidian-mdtex-plugin)

## MdTex導入方法-v2.0.0

[obsidian-mdtex-plugin.zip](https://github.com/Mekann2904/obsidian-mdtex-plugin/releases/download/v2.0.0/obsidian-mdtex-plugin.zip)をダウンロードし、展開する。

設定に移動し、矢印のフォルダーアイコンをクリックする。  
先ほど展開したファイルを移動させる。

[![画像](https://assets.st-note.com/img/1737125894-B3LOCMhfW0uSm7ZK19bTXkQv.png?width=1200)](https://assets.st-note.com/img/1737125894-B3LOCMhfW0uSm7ZK19bTXkQv.png?width=2000&height=2000&fit=bounds&quality=85)

この状態でMdTexプラグインはインストールされた。

## 環境構築

ここで紹介する方法はMacを想定している。  
他の環境でも同様にLualatexが使える様になっていれば良い。

### MacTex

[MacTeX - TeX Users Group](https://tug.org/mactex/)に移動し、[**MacTeX Download Page**](https://tug.org/mactex/mactex-download.html)から落としたインストーラーで**MacTeX**の環境が構築できる。

  

[![画像](https://assets.st-note.com/img/1737125930-Nr13lgV4qhAP7CeQGItkKWSx.png?width=1200)](https://assets.st-note.com/img/1737125930-Nr13lgV4qhAP7CeQGItkKWSx.png?width=2000&height=2000&fit=bounds&quality=85)

簡単に環境構築できるため、詳しい導入方法は割愛させていただく。

### pandoc-crossref

```
pip install pandoc-crossref
```

copy

をターミナルから実行するだけで良い。

詳しくは、公式レポジトリを参照。  
[GitHub - lierdakil/pandoc-crossref: Pandoc filter for cross-references](https://github.com/lierdakil/pandoc-crossref)

### LaTeXパッケージ

MacTexで導入されているはずだが、足りない場合は追加すれば動くはずだ。

  

## ObsidianのMdTexプラグイン設定

出力するためには以下の項目が正しく設定されている必要がある。

- Pandocのパス
    
- 検索ディレクトリのパス
    
- pandoc-crossrefのパス
    
- LaTeXエンジン
    

パスを検索するには以下のコマンドを使うと良い。

```
$ which pandoc
$ which pandoc-crossref 
$ which lualatex
```

copy

検索ディレクトリのパスはユーザが指定しなければならない。  
(注意:デフォルトだと画像が取得されない。)  
おすすめはobsidianの保管庫のパス。

## 使用方法

なるべく手を加えないで出力できるようにしている。相互参照など、特殊な場合は独自の方法で記述する必要がある。相互参照は入力補完があるため難しくないはず。

基本的な文法は以下に載せておくため、つまずいたら確認してほしい。

表紙を作成するためにはYAMLを記述。  
目次を作成するためには\tableofcontentsを記述。  
相互参照しない場合はラベルやキャプションがなくても動作する。

````

---
title: Markdownでの相互参照方法
author: Mekann
date:
  - 2025-01-16
---
\clearpage
\tableofcontents
\clearpage

# Markdownでの相互参照方法


## 1. **画像**

![[c6-1.png]]{#fig:label width=40%}[適当なグラフ]


参照:  [@fig:label]

## 2. **コードブロック**

```python {#lst:label caption="コード例"}
print("Hello, World!")
```


参照:  [@lst:label]



```python {#lst:la caption="コード例"}
print("Hello, World!")
```


[@lst:la]

## 3. **表**

| 列1   | 列2   |
| ---- | ---- |
| データ1 | データ2 |
: 表の説明 {#tbl:label}

参照:  [@tbl:label]


## 4.**数式**


$$
E = mc^2
$$
{#eq:label}


[@eq:label]

````

copy

[

**Markdownでの相互参照方法.pdf**

67.9 KB

ファイルダウンロードについて

ダウンロード



](https://note.com/api/v2/attachments/download/266d5ad2086fb01248e74e2b879a276c)

### PDFエクスポートの方法

1. 左のリボンにある文書アイコンをクリックする
    
2. コマンドパレットから検索する(mdtexと入力)
    

### エラー対処

どうしてもうまく動かない場合は、エラーを開発者モードで確認することができる。  
  
Windowsでは【Ctrl + Shift + I】  
Macでは【Command + Option + I】