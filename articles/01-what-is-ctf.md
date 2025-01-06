---
title: "【ポエム】CTFってまじで何？？？"
emoji: "🏁"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [ポエム, security]
published: true
publication_name: "nitic_students"
---

## まえがき

@[speakerdeck](1a0af2b432224dcca3a2a6d4c48aa612)

先日、[茨城高専](https://www.ibaraki-ct.ac.jp)の学生団体[neo わくわくクラブ](https://instagram.com/neo_wakuwaku_club)の第 1 回 LT 会が行われました。
ここではその時私が話した内容と、時間の関係上話せなかった CTF に関する詳しい話をしたいと思います。
上の SpeakerDeck と見ながら読んでいただくと理解しやすいです。

## CTF とは？？

**C**apture **T**he **F**lag の略称で、仮想環境で行われる旗取りゲームです。
個人でも、チームでも参加可能で、セキュリティーに関する攻撃と防御の両方を学ぶことができるため、近年注目されています。

## 主な形式

> - **Jeopardy 形式**：カテゴリー別の問題を解き、難易度に応じたポイントを獲得
>   - Web セキュリティ、フォレンジックス、暗号理論、リバースエンジニアリング、バイナリ解析など多彩なカテゴリー
> - **Attack & Defense 形式**：リアルタイムの攻防戦で、自身のサーバーを防御しつつ他チームを攻撃
>   - チームワークと戦略性が求められる

Jeopardy 形式はいわゆるクイズ形式で、最も一般的です。初心者の方でも比較的わかりやすく練習もしやすいため、始めるならこちらからです。
対して、Attack & Defence 形式は、皆さんが想像するようなハッキング対決で、リアルタイムの攻防戦が見どころです。なかなか大会は行われていません。

## なぜ CTF をやるのか？

CTF には大きく分けて 3 つほどの魅力があります。

**1\. スキルアップにつながる**
CTF は実践形式で行われているため、現場で役立つ知識や技術を学ぶことができます。

**2\. 楽しさと挑戦**
難し目な、解きごたえのある問題がおおいため、達成感があります。また、スコアが表示されるため、ゲーム感覚で楽しむことができます。

**3\. コミュニティとのつながり**
多くの場合、CTF はチーム戦であるため、仲間と協力して教え合いながら行います。

## 学べるスキル

- **リバースエンジニアリング**
  CTF の基礎となる分野です。具体的には、バイナリから文字列を抽出したりします。

- **エクスプロイト開発**
  皆さんが想像するハッキングそのものです。比較的 Attack & Defense 形式に多く見られます。

- **暗号学**
  暗号解読や RSA 暗号の知識が身につきます。Base64 などの初歩的な知識で解ける問題もあれば、思いつきが必要な問題まで幅広く、奥が深いです。

- **フォレンジフォックス**
  データ復元やメモリ解析を行う分野です。リモートデスクトップのキャッシュファイルの解析など、一見不可能そうな問題が多いです。

- **ウェブセキュリティ**
  こちらは両方の形式で見られる分野です。用意されたウェブサーバーから SQL コマンドを使用してフラグを取得したりします。

- **プログラム**
  ガッツリ数学みたいなことをする問題です。私が一番苦手な分野の一つです。競プロ普段からやってる人は得意そうです。

- **トリビア**
  これだけは例外で、いろいろな問題が組み合わさった、本当に色々な種類の問題が出ます。量子の概念やアドレスの法則など様々な知識が必要になるため、解けた時には本当に喜びます。

## サンプル問題

初めての方でもわかりやすいように、簡単な問題を２つほど作成しました！
ぜひ取り組んでみてください

:::message
基本的には、CTF では検索や AI への質問は禁止されていません。むしろ困ったら AI に聞いたほうがいいです。
ですが、大会などでは、**一時チャットモード**にしておきましょう。
基本的には大会の問題は、他者への公開が禁止されているので AI の学習も公開と同じことであるためです。
:::

### 問題 1: 基本的な暗号解読

> **説明:**
> 以下の暗号文を解読し、フラッグ形式 `flag{...}` で答えを提出してください。
>
> ```base64
> U2VjdXJpdHlJc1Bvd2Vy
> ```

**キーワード:**
:::details キーワード
Base64 デコード
:::

**ヒント:**

:::details ヒント
この暗号文は Base64 エンコードされています。
オンラインでは、Dencode、コマンドラインでは base64 コマンドを使うのがおすすめです
:::

### 問題 1: 解説

:::details 解説
Base64 デコードすると `SecurityIsPower` が得られます。
よって、フラグは `flag{SecurityIsPower}` となります。

オンラインツールや以下のコマンドで解けます：

```bash
echo "U2VjdXJpdHlJc1Bvd2Vy" | base64 -d
```

::: details 解答

```plaintext
flag{SecurityIsPower}
```

:::

こちらは、暗号学の分野に当たります。実際には Base64 という指定もなく、自分で判断したりします。

---

### 問題 2: 暗号学の基礎

> **説明:**
> 以下の暗号文を解読し、フラッグ形式 `flag{...}` で答えを提出してください。
>
> ```hex
> 52 65 76 65 72 73 65 20 45 6e 67 69 6e 65 65 72 69 6e 67
> ```

**キーワード:**

:::details キーワード

- 16 進数 文字 変換

:::

**ヒント:**

:::details ヒント

- 16 進数（Hex）エンコードされています。ASCII 文字に変換してみましょう。
  オンラインでは Dencode、コマンドラインでは Python を使用するのがおすすめです。

:::

### 問題 2: 解説

::: details 解説
16 進数の各バイトを ASCII 文字に変換すると `Reverse Engineering` が得られます。
よって、フラグは `flag{ReverseEngineering}` となります。

Python の場合

```python
bytes.fromhex("52 65 76 65 72 73 65 20 45 6e 67 69 6e 65 65 72 69 6e 67").decode()
```

:::details 解答

```plaintext
flag{ReverseEngineering}
```

:::

こちらは、リバースエンジニアリングにあたります。2 進数や 16 進数は CTF の基本中の基本です。

---

問題は以上です。いくつ解けたでしょうか。

## CTF を始めるには

CTF の問題を練習したり、セキュリティに関する学習ができるサイトはたくさんありますが、特にオススメなのは、以下のサイトです。

- [CTF Time](https://ctftime.org)：世界中の CTF 情報が集約しています。大会情報やその結果など、たくさんの情報が乗っています。
- [CpawCTF](https://ctf.cpaw.site/)：初心者に優しい問題(日本語)が多数あります。
問題も比較的簡単ながらも、解きごたえのある問題が多いです。
- [OverTheWire](https://overthewire.org)：サーバーとセキュリティの基礎を学習できます。
Linux の操作やコンピューターセキュリティなどを実践的に学部ことができます。
- [TryHackMe](https://tryhackme.com)や[Hack The Box](https://hackthebox.eu)：仮想環境でのハッキング演習を行うことができます。
中級者から上級者向けの問題が多く、Attack & Defense 形式の練習には最適です。

## 身近な CTF の大会

- SECCON CTF: 日本で最も規模が大きい CTF の大会。
- LINE CTF:LINE ヤフー株式会社主催の大会。**賞金１万ドル**(2024 年度)

などこの他にも、都道府県の警察本部が企画している大会などもあります。ぜひ、自分の住んでいる地域の大会についても調べてみてください。

:::message
2012 年度、東京電機大学で開催された**SECCON CTF 全国大会**で、警察からのスカウトが行われたと報道されています。
ホワイトハッカーを目指している人にもおすすめです。
:::

## 💡 まとめ

- **CTF は学びと成長の場**
  - 多岐にわたる技術分野を網羅し、実践的なスキルを身につけられる
- **楽しみながらスキルアップ**
  - ゲーム感覚でセキュリティを学べるので、達成感を得られる
- **今すぐ始めよう！**
  - 最初の一歩を踏み出して、サイバーセキュリティの世界へ飛び込もう！

---

## 特別問題: リバースエンジニアリング

> **説明:**
> 以下のバイナリファイルを解析し、フラグ形式 `flag{...}` で答えを提出してください。
>
> [ダウンロードリンク](https://github.com/fukayatti0/neowaku-LT/raw/refs/heads/main/vol-1/Questions/Question3/DecodeBinary)

**ヒント:**

::: details ヒント

- `strings` コマンドと `grep` コマンドを使ってバイナリ内の文字列を確認してみましょう。
  フラグは flag{...}という形で隠されています

:::

### 特別問題: 解説

::: details 解説

バイナリファイル内の文字列を検索することで、フラグを見つけることができます。

コマンド実行：

```bash
strings DecodeBinary | grep flag
```

このコマンドにより `flag{NEO_wakuwaku_club}` が得られます。

::: details 解答

```plaintext
flag{NEO_wakuwaku_club}
```

:::

これは、バイナリ解析の基本的なテクニックの一つで、実際の CTF でもよく使用される手法です。
本当によく使うテクニックなので、知っておいて損はないです。

---

## あとがき

実際のところ、私は 2〜3 ヶ月に CTF を始めたばかりでまだまだ初心者です。しかし、友達が県警の大会で表彰されたり、もとから Linux を触っていたこともあり、やってみようということになり始めました。
今となっては、プログラミング関係のコンテストで一番好きなものになっています。
きっかけは何でもいいです。
CTF の世界はとても奥が深いので、ぜひ挑戦してみてください！！

[こちらのリポジトリ](https://github.com/fukayatti0/neowaku-LT/tree/main/vol-1)に、今回作成した問題やその解き方などをまとめておきました。
ぜひ見てみてください！！

---

次回の LT 会では詐欺サイトの特徴についてでも話そうと思います！