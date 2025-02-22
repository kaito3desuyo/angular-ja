# Angularのバージョンとリリース

私たちはAngularフレームワークには安定性が必要であると認識しています。安定性によって、再利用可能なコンポーネントやライブラリ、チュートリアル、ツール、学習されたプラクティスが予期せず時代遅れになることはありません。 Angularが発展するまわりのエコシステムには安定性が不可欠です。

また、Angularが進化を続けたいという願望も共有しています。私たちは、あなたが構築している基盤が継続的に改善されていること、そしてその他のウェブ・エコシステムとユーザーのニーズを常に最新の状態に保てることを確実にするよう努めています。

このドキュメントには、安定性とバランスのとれた最先端のアプリケーション開発プラットフォームを提供するために私たちが従うプラクティスが含まれています。私たちは将来の変化が常に予測可能な方法で導入されるように努めています。 Angularに依存しているすべての人に、新しい機能が追加される時期と方法を知り、時代遅れの機能が削除されたときに十分に準備されることを願っています。


<div class="alert is-helpful">

このドキュメントで説明するプラクティスは、Angular 2.0以降に適用されます。現在AngularJSを使用している場合は、[AngularJSからのアップグレード](guide/upgrade "Upgrading from Angular JS")を参照してください。 _AngularJS_はすべてのv1.xバージョンのAngularの名前です。

</div>


{@a versioning}
## Angularのバージョニング

Angularのバージョン番号は、リリースで導入された変更のレベルを示します。この[セマンティックバージョン](https://semver.org/ "Semantic Versioning Specification")管理を使用すると、新しいバージョンへの更新の潜在的な影響を理解するのに役立ちます。

Angularのバージョン番号には3つの部分があります: `major.minor.patch`。たとえば、バージョン7.2.11は、メジャーバージョン7、マイナーバージョン2、およびパッチバージョン11を示します。

バージョン番号は、リリースに含まれる変更のレベルに基づいて増えていきます。

* **メジャーリリース** には重要な新機能が含まれていますが、更新には最小限の開発者の協力が求められます。新しいメジャーリリースにアップデートするときは、アップデートスクリプト、リファクタリングコード、追加テストの実行、新しいAPIの学習が必要な場合があります。


* **マイナーリリース** には新しい小さな機能が含まれています。マイナーリリースは完全に後方互換性があります。アップデート中に開発者の協力は必要ありませんが、リリースで追加された新しいAPI、機能、および機能を使用するようにアプリケーションやライブラリを修正することもできます。サポートされているバージョンを拡張することで、マイナーバージョンのピア依存関係を更新しますが、プロジェクトにこれらの依存関係を更新を求めることはありません。


* **パッチリリース** は低リスクなバグ修正リリースです。更新中に開発者の協力は求められません。

<div class="alert is-helpful">

**Note:** As of Angular version 7, the major versions of Angular core and the CLI are aligned. This means that in order to use the CLI as you develop an Angular app, the version of `@angular/core` and the CLI need to be the same.

</div>

{@a updating}
### サポートされているアップデートパス

次の条件を満たしていれば、どのバージョンのAngularにも`ng update`することができます。

*   アップデート*先*のバージョンがサポートされている
*   アップデート*元*のバージョンがアップデート先のバージョンの
    1メジャーバージョン以内であること

たとえば、バージョン 11 からバージョン 12 へのアップデートは、バージョン 12 がまだサポートされている場合に可能です。
複数のメジャーバージョンにまたがるアップデートを行う場合は、1メジャーバージョンごとにアップデートを行ってください。
たとえば、バージョン 10 からバージョン 12 にアップデートする場合。

1. バージョン10からバージョン11にアップデートする
1. バージョン11からバージョン12にアップデートする

Angularプロジェクトを最新バージョンにアップデートする方法の詳細については、[最新に保つ](guide/updating "Updating your projects")を参照してください。


{@a previews}
### プレビューリリース

個々のメジャーリリースとマイナーリリースごとに、"Next"リリースとリリース候補版（`rc`）を提供することで、今後の展開を先取りできるようにしています。

* **Next:** 活発な開発とテストの下にあるリリース。ベータリリースは、`8.0.0-beta.0` のように `beta` 識別子を付加したリリースタグで示されます。

* **リリース候補:** 機能が完成し最終テストが行​​われているプレリリース。リリース候補版は、バージョン `8.1.0-rc` のように、`rc` 識別子が付加されたリリースタグで示されます。

次期バージョンのドキュメントは [next.angular.io](https://next.angular.io) から入手できます。これには、ベータ版またはリリース候補の機能およびAPIに関するすべての資料が含まれます。


{@a frequency}
## リリース周期

定期的なリリーススケジュールに向けて作業を進めており、Angularの進化と共にアップデートを計画し、調整することができます。

<div class="alert is-helpful">

日付は一般的なガイダンスとして提供されており、変更される場合があります

</div>

基本的に、次のリリースサイクルが予想されます。

* 6か月ごとのメジャーリリース

* メジャーリリースごとに1回から3回のマイナーリリース

* ほぼ毎週のパッチリリースとプレリリース（`next`または`rc`）

この一連のリリースにより、熱心な開発者は、十分に開発され、コードレビューおよび統合テストプロセスを経てすぐに新機能にアクセスできるようになります。プレリリースビルドを使用するGoogleおよびその他の開発者によって検証されています。


{@a lts}
{@a support}
## サポートポリシーとスケジュール

<div class="alert is-helpful">

推定される日付は一般的なガイダンスとして提供されており、変更される場合があります

</div>

### リリーススケジュール {@a release-schedule}

| Version | Date               |
|:--------|:-------------------|
| v16.1   | Week of 2023-06-12 |
| v16.2   | Week of 2023-08-07 |
| v17.0   | Week of 2023-11-06 |

### サポート期間 {@a support-window}

すべてのメジャーリリースは原則として18か月間サポートされます。

* 上記の[リリース周期](#frequency "Release frequency")で説明したように、定期的にスケジュールされたアップデートとパッチがリリースされる、6ヶ月の*アクティブサポート*。

* 12ヶ月の*長期サポート（LTS）*。LTS期間中は、[重要な修正とセキュリティパッチ](#lts-fixes)のみがリリースされます。

### 現在サポート中のバージョン {@a actively-supported-versions}

次の表は、サポート対象のAngularバージョンのステータスを示しています


| バージョン | 状態 | リリース     | アクティブの終了  | LTSの終了|
|:--------|:-------|:-----------|:------------|:-----------|
| ^16.0.0 | Active | 2023-05-03 | 2023-11-03  | 2024-11-08 |
| ^15.0.0 | LTS    | 2022-11-18 | 2023-05-03  | 2024-05-18 |
| ^14.0.0 | LTS    | 2022-06-02 | 2022-11-18  | 2023-11-18 |

Angularバージョン v2 から v13 のサポートは終了しました。

### LTS の修正 {@a lts-fixes}

原則として、LTSバージョンでは次のいずれかを解決するものが修正とみなされます。

* 新たに確認されたセキュリティ上の脆弱性
* LTS開始以降、ブラウザの新バージョンなどサードパーティの変更に起因して発生したリグレッション

{@a deprecation}
## 廃止のプラクティス {@a deprecation-practices}


新しいベストプラクティスへの変更、依存関係の変更、（Web）プラットフォーム自体の変更と共に最新の状態に保つため、そして革新のために、ときには&quot;破壊的変更&quot;選択したAPIや機能のサポートの削除などが必要になります。

これらの移行をできるだけ簡単にするために、私たちはこれらの約束をしています。

* 私たちは、変化の激しさを最小限に抑え、可能な限り移行ツールを提供するために努めています。

* ここで説明している廃止方針に従い、アプリケーションを最新のAPIとベストプラクティスに更新するための時間を確保します。

更新に十分な時間と明確なパスがあることを確認するための、非推奨化のポリシーはこちらです。

* **告知:** [チェンジログ](https://github.com/angular/angular/blob/main/CHANGELOG.md "Angular change log") に廃止予定のAPIおよび機能をお知らせします。廃止予定のAPIは、 [ドキュメンテーション](api?status=deprecated) に取り消し線付きで記載されています。廃止予定を発表した場合は、推奨されるアップデートパスも発表します。便利になるように、 [非推奨リスト](guide/deprecations) には廃止予定のAPIと機能の要約が含まれています。


* **非推奨期間:** APIまたは機能が非推奨になっても、それは続く2つのメジャーリリースには引き続き存在します。その後、廃止予定のAPIおよび機能は削除の候補になります。廃止予定はどのリリースでも発表できますが、廃止予定のAPIまたは機能の削除はメジャーリリースでのみ発生します。廃止予定のAPIまたは機能が削除されるまで、LTSサポートポリシーにしたがって維持されます。つまり、重大な問題とセキュリティの問題のみが修正されます。


* **npm依存関係:** アプリケーションの変更を必要とするnpm依存関係の更新は、メジャーリリースでのみ行います。マイナーリリースでは、サポートされているバージョンを拡張してピアの依存関係を更新しますが、これらの依存関係を更新するようにプロジェクトに要求することは将来のメジャーバージョンまでありません。つまり、Angularのマイナーリリースでは、Angularアプリケーションおよびライブラリ内のnpm依存関係の更新はオプションです。




{@a public-api}
## 公開API

Angularは、多くのパッケージ、サブプロジェクト、ツールのコレクションです。プライベートAPIの偶発的な使用を防ぐために（ここで説明するプラクティスの対象を明確に理解できるように）私たちは公開APIと見なされるものとそうでないものを明文化します。詳細については、[Angularでサポートされている公開API](https://github.com/angular/angular/blob/main/docs/PUBLIC_API.md "Supported Public API Surface of Angular")を参照してください。

公開APIのあらゆる変更は、上述のバージョニング、サポート、および非推奨化ポリシーが適用されます。

<a id="developer-preview"></a>

## 開発者プレビュー（Developer Preview）

たまに、「Developer Preview」というラベルで新しいAPIを紹介することがあります。これらは、十分に機能し、洗練されたAPIですが、私たちの通常の非推奨化ポリシーで安定化する準備ができていません。

これは、安定化する前に実際のアプリケーションからフィードバックを集めたい、あるいは関連するドキュメントや移行ツールが完全に完成していないのが理由です。

このドキュメントで説明されているポリシーとプラクティスは、Developer PreviewとマークされたAPIには適用されません。そのようなAPIは、フレームワークの新しいパッチバージョンであっても、いつでも変更されます。Developer Preview APIを使用する利点が、通常のセマンティック・バージョニングの利用から外れた破壊的変更のリスクに見合うかどうかは、チームで自己判断する必要があります。

<!-- links -->

<!-- external links -->

<!-- end links -->

@reviewed 2023-05-03
