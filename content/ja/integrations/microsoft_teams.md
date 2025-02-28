---
categories:
- コラボレーション
- ネットワーク
- 通知
dependencies: []
description: Microsoft Teams で Datadog アラートとイベントの通知を受信
doc_link: https://docs.datadoghq.com/integrations/microsoft_teams/
draft: false
git_integration_title: microsoft_teams
has_logo: true
integration_id: ''
integration_title: Microsoft Teams
integration_version: ''
is_public: true
kind: インテグレーション
manifest_version: '1.0'
name: microsoft_teams
public_title: Datadog-Microsoft Teams インテグレーション
short_description: Microsoft Teams で Datadog アラートとイベントの通知を受信
version: '1.0'
---

## 概要

Microsoft Teams と統合して、以下のことができます。

- Microsoft Teams で Datadog アラートとイベントの通知を受信
- Microsoft Teams の中からインシデントを管理することができます。

## Microsoft Teams チャンネルへのモニター通知の送信

### セットアップ

Datadog を Microsoft Teams チャンネルと統合するには、以下のようにします。

1. チャンネルのリストで、チャンネル名の横にある `...` ボタンを選択し、**Connectors** を選択します。

    {{< img src="integrations/microsoft_teams/microsoft_team_step_1_v2.png" alt="Microsoft Teams 手順 1" >}}

2. Datadog を検索し、**Configure** をクリックします。

    {{< img src="integrations/microsoft_teams/microsoft_team_step_2_v2.png" alt="Microsoft Teams 手順 2" >}}

3. コネクタ構成モーダルで、Webhook URL をコピーします。
4. Datadogで、[**Integrations > Microsoft Teams**][1] の順に移動します。
5. Configuration タブで、**Add Channel** をクリックしてチャンネルに名前を付け、webhook URL を貼り付けます。
6. コネクタ構成モーダルで、**Save** をクリックします。

### 使用方法

Datadog モニターから、[`@-notification` 機能][2]を使用して、Microsoft Teams に通知を送信します。通知を `@teams-<CHANNEL>` というアドレスに送信し、`<CHANNEL>` を Microsoft Teams のチャンネル名に置き換えます。

## Microsoft Teams における Datadog Incident Management

<div class="alert alert-warning">
Datadog Incident Management for Microsoft Teams は公開ベータ版で、US1 サイトでのみ利用可能です。
</div>

### アカウント設定

まず、Microsoft Teams に Datadog アプリをインストールします。

1. Microsoft Teams を開きます。
2. 垂直ツールバーの **Apps** をクリックします。
3. "Datadog" を検索し、タイルをクリックします。
4. Datadog アプリをインストールするには、**Add** をクリックします。

{{< img src="integrations/microsoft_teams/microsoft_teams_install_datadog_app_in_teams.png" alt="Microsoft Teams の Datadog インストールアプリタイル" >}}

次に、Microsoft のテナントを Datadog に接続します。

1. Datadog で、[Microsoft Teams Integration Tile][1] に移動します。
2. **Add Account** をクリックすると、Microsoft に移動します。
3. 画面の指示に従って、**OK** をクリックします。

Datadog Incident Management の機能の中には、インシデントごとに新しいチームを作成するなど、テナント上でアクションを実行するものがあり、権限が必要になります。Datadog がこれらのアクションを実行することを認可するには、*Global Admin* ロールを持つ人が次のステップを完了する必要があります。

1. Datadog で、[Microsoft Teams Integration Tile][1] に移動します。
2. **Authorize** をクリックすると、Microsoft に移動します。
3. 画面の指示に従って、**OK** をクリックします。

### ユーザー設定

Microsoft Teams から Datadog のアクションを実行するには、Datadog と Microsoft Team のアカウントを接続する必要があります。

Microsoft Teams からアカウントを接続するには

1. Microsoft Teams を開きます。
2. 垂直ツールバーの `...` ボタンをクリックし、Datadog を選択すると、Datadog ボットとのチャットが開始されます。
3. "accounts" と入力し、エンターキーを押します。
   {{< img src="integrations/microsoft_teams/microsoft_teams_connect_account_from_teams.png" alt="Microsoft Teams からのアカウント接続" >}}

4. Datadog ボットが、アカウントの接続方法について応答します。**Connect Datadog Account** をクリックします。
5. その後、Datadog ボットが、アカウントを接続するためのリンクが含まれたメッセージを送信します。リンクをクリックし、プロンプトに従います。
6. [Microsoft Teams Integration Tile][1] へと戻ります。
7. [Microsoft Teams Integration Tile][1] のプロンプトで **Create** をクリックし、アプリケーションキーを作成します。



Datadog からアカウントを接続することも可能です。

1. Datadog で、[Microsoft Teams Integration Tile][1] に移動します。
2. 表示されたテナントの中から、**Connect** をクリックします。
3. 画面の指示に従って、**OK** をクリックします。
4. [Microsoft Teams Integration Tile][1] へと戻ります。
5. 上記のプロンプトで **Create** をクリックし、アプリケーションキーを作成します。

{{< img src="integrations/microsoft_teams/microsoft_teams_connect_account_from_datadog_v2.png" alt="Datadog Microsoft Teams インテグレーションタイルからアカウントを接続します" >}}

### 使用方法

Microsoft Teams から新しいインシデントを宣言するには

1. 任意のチームで会話を開始します。
2. `@Datadog` と入力するか、`...` ボタンで **Messaging extensions** メニューを開き、**Datadog** アプリを選択します。
3. **Create an Incident** を選択します。
4. 希望の情報をフォームに入力します。
5. **作成**をクリックします。

Datadog へのアクセス権の有無を問わず、Microsoft Teams テナント内の誰でもインシデントを宣言できます。

新しいインシデントが作成されると、`incident-( 一意の番号 ID )` という名前の対応するチームが作成されます。

インシデントを更新するには、作成と同様の手順で行います。

1. インシデントチームにいながら、会話を始めます。
2. `@Datadog` と入力するか、`...` ボタンで **Messaging extensions** メニューを開き、**Datadog** アプリを選択します。
3. **Update Incident** を選択します。
4. 希望の情報をフォームに入力します。
5. **Update** をクリックします。

次を使用してオープン（アクティブで安定している）インシデントをリスト表示します。

```
@Datadog list incidents
```

インシデントチーム内のメッセージの右端にある "More actions" メニューを使用すると、そのメッセージをインシデントタイムラインに送信することができます。

#### インシデントの更新チャンネル
インシデント更新チャンネルを使用すると、関係者は Microsoft Teams から直接、すべてのインシデントのステータスを組織全体で確認することができます。これらのアップデートを投稿するチームとチャンネルをアカウントで選択すると、チャンネルは次の投稿を受け取ります。

   - 新しく宣言されたインシデント。
   - 重要度、ステータスの移行、インシデントコマンダーへの変更点。
   - アプリ内のインシデントの概要ページへのリンク。
   - インシデント専門チームへの参加リンク。

Microsoft Teams アプリがインストールされたら、**Incident Settings** ページに移動できます。ここから、**Incident Updates** Channel セクションまでスクロールダウンし、セットアップフローを開始することができます。

#### インシデントチャンネルの設定方法

1. [Incidents Settings][3] に移動します。
2. Microsoft Teams インテグレーションの **Incident Updates Channel** セクションを探します。
3. インシデントアップデートのために、正しいテナント、チーム、チャンネルを選択します。

{{< img src="integrations/microsoft_teams/ms_teams_incident_updates.png" alt="Microsoft Teams インシデントアップデートチャンネル設定。" >}}

## 収集データ

### メトリクス

Microsoft Teams インテグレーションは、メトリクスを提供しません。

### イベント

Microsoft Teams インテグレーションには、イベントは含まれません。

### サービスチェック

Microsoft Teams インテグレーションには、サービスのチェック機能は含まれません。

## トラブルシューティング

### SSO の使用

次の手順を使用して、新しいチャンネルコネクターを設定します。

1. Datadog にログインし、セットアップ手順 1 および 2 を完了します。

2. セットアップ手順 3 で MS Teams ページから Datadog にリダイレクトされたら、新しいタブを開き、SSO で Datadog にログインします。次に、セットアップ手順 4 を個別に実行します。

ご不明な点は、[Datadog のサポートチーム][4]までお問合せください。

[1]: https://app.datadoghq.com/account/settings#integrations/microsoft-teams
[2]: https://docs.datadoghq.com/ja/monitors/notifications/#notification
[3]: https://app.datadoghq.com/incidents/settings#Integrations
[4]: https://docs.datadoghq.com/ja/help/