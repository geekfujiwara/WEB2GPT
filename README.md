# WEB2GPT (Web検索から回答作成)

> [!Note]
> AI Builder AI プロンプトとして、[GPT の機能が日本でも利用できるようになりました](https://learn.microsoft.com/ja-jp/ai-builder/availability-region)。
> 日本でのAI プロンプトの利用は[地域間のデータ移動を有効化する](https://learn.microsoft.com/ja-jp/power-platform/admin/geographical-availability-copilot#enable-data-movement-across-regions)必要があります。
> また、動いたよ、できたよという結果は是非、 [ギークフジワラのXアカウント](https://x.com/Geekfujiwara) までメンションしてご報告ください！！

Bing Search API でWebの検索結果を生成AI により要約して回答し、Dataverse に保存ができるPower Apps のアプリケーションです。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/52b655d7-13c1-4e14-b6e3-f94744f1e824)

レスポンシブデザインに対応しており、スマホ縦レイアウトでは最低限の情報だけ表示されるようになります。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/023a45f4-07c6-4c1f-a1b6-97456c3e6010)

過去に登録されたナレッジも見たい場合は横向きのレイアウトにすると見えるようになっています。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/c8e1eb2d-c3bc-453a-a49a-e88ef179c844)

広く一般の公開情報に対して情報収集して要約することが可能なため、様々な分野で利用することが出来ます。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/d6f9457c-325b-4267-a4ae-91bf3685dbf1)

生成AI は間違いを起こすことがあるため、実際の検索結果を確認することが出来るようになっています。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/8d430af6-96a4-4727-becb-00bcb62afa81)

作成した回答はナレッジとして保存することが出来ます。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/887dcee3-237b-4955-b566-09e385c95213)




# 事前準備

事前に以下を行う必要があります。

* [AI Builder が利用可能なライセンスを入手する](https://powerapps.microsoft.com/ja-jp/pricing/)
* [地域間のデータ移動を有効化する](https://learn.microsoft.com/ja-jp/power-platform/admin/geographical-availability-copilot#enable-data-movement-across-regions)
* [Azure を無料で始める](https://azure.microsoft.com/ja-jp/pricing/free-services/)

# インポート方法

## Bing Search API 

[Bing Search API](https://www.microsoft.com/en-us/bing/apis/bing-web-search-api)を準備します。

無償で利用できる枠が提供されていますのでそのプランでサインアップして試すことが出来ます。

### Bing Search API 無料枠の条件

* トランザクション上限1,000回/月
* 3回/秒 

[無料枠の条件](https://www.microsoft.com/en-us/bing/apis/pricing)

> [!Note]
> サポートが必要な本番環境での利用では有償のプランをご検討ください。

### リソースの作成方法

Bing search リソースを検索して新規作成します。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/19729265-7600-46b9-8db3-66e24dab4994)

作成できましたらキーを入手します。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/bae89571-a1ec-4178-875a-01f9967ceec6)

キーはこちらから入手できます。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/907595bb-4124-42fa-8bf8-5103173f0918)

## Power Apps ソリューション

Power Apps のソリューションは[リリース](https://github.com/geekfujiwara/WEB2GPT/releases/tag/1.0.0.0)から入手できます。

ソリューションのインポートを行います。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/490bf108-f23b-4d56-a5d1-0e75e71dfd39)

リリースから入手したソリューションファイルをアップロードします。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/49a5b94c-6a57-4398-a3af-03475223a35e)

次へに進みます。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/dc1bd06c-ee63-40ba-b364-5d5589ea3856)

インポート時にBing Search API のKeyを問われますので入力します。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/159ce233-c225-42ed-9d62-4ad1cecaf7b3)

> {!Note}
> インポート後に言語のラベルが不足している旨の警告が出ても問題ありません。
> ![image](https://github.com/geekfujiwara/WEB2GPT/assets/96101315/35b1c7c8-a882-48bb-8c3c-6541ff1a0353)

マネージドソリューションをインポートした場合、マネージドソリューションのタブにソリューションが存在しています。

![image](https://github.com/geekfujiwara/WEB2GPT/assets/96101315/8131df77-c449-4464-bc64-7265a332ad94)

インポート後、すべてのカスタマイズを公開してください。

![image](https://github.com/geekfujiwara/WEB2GPT/assets/96101315/c91be7b8-95f6-4981-996b-c22d4af0b34d)

# アプリの利用方法

アプリを起動します。

![image](https://github.com/geekfujiwara/WEB2GPT/assets/96101315/1d948b27-25a8-4c48-b5c8-34dfb8a429e0)


サンプルの質問として以下を入力してみます。

> [!Note]
> 自由に質問を入力してみてください。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/16e16642-6b5c-44c2-bc00-3f4a9254bd89)


入力後、回答案の生成をさせてみます。
![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/91e07730-82a2-4d18-843e-973f59e44cf2)

検索と生成に少々時間を要します。作成中はアプリの操作ができないように読み込み画面に切り替わります。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/625c3014-2720-4133-890f-714bff3ac056)

生成AIにより回答が生成されました。参考にしたリンクも同時に返してくれています。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/75b1ee6f-d977-4860-b592-8ea1c07fa3a2)

保存に成功すると左側のメニューに表示されます。

> [!Note]
> 実際にはDataverseに保管されています。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/247d5875-29f2-4b01-a511-c6abe841a52d)

検索結果も確認することが出来ます。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/8cd66a16-6632-4f16-8d6a-c18baa1ffa07)

# 仕様説明

## AI Builder AI プロンプト

AI Builder では以下のようなAI プロンプトを作成しています。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/33e74dfc-3e44-409f-98e2-8212854bb711)


## Power Automate でのBing Search

Power Automate で検索処理を設定しています。

HTTPリクエストの部分がBing Search API の部分です。

![image](https://github.com/geekfujiwara/GenerativeAI-WebSearchAnswer/assets/96101315/392878fc-3e8b-489f-b3aa-f885b2fb35d5)



# リファレンス

* [Bing Custom Search API](https://learn.microsoft.com/ja-jp/bing/search-apis/bing-web-search/reference/headers)
* [Power Apps ソリューションインポート方法](https://learn.microsoft.com/ja-jp/power-apps/maker/data-platform/import-update-export-solutions)

