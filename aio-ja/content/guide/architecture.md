# Angularの概念の紹介

Angularは、HTMLとTypeScriptでシングルページクライアントアプリケーションを開発するためのプラットフォームであり、そしてフレームワークです。
Angularはそれ自身がTypeScriptで書かれています。
コア部分およびオプショナルな機能を、アプリケーションにインポートするTypeScriptライブラリのセットとして実装しています。

Angularアプリケーションのアーキテクチャは、いくらかの基本概念に依存しています。
Angularフレームワークの基本的な構成要素は、*NgModules* で組織されたAngularコンポーネントです。 
NgModuleは、関連するコードを機能セットに集めます。 Angularアプリケーションは、一連のNgModuleによって定義されます。
アプリケーションには常に、ブートストラップを可能にする少なくとも1つの*ルートモジュール*があり、通常はさらに多くの*機能モジュール*があります。

* コンポーネントは *ビュー* を定義します。ビューは、プログラムのロジックとデータの中からAngularが選択し、変更できる画面要素のセットです。すべてのアプリケーションには、少なくともルートコンポーネントがあります。

* コンポーネントは、ビューに直接関係しない特定の機能を提供する *サービス* を使用します。サービスプロバイダーは、 *依存性* としてコンポーネントに *注入* することができ、コードをモジュール化し、再利用可能で効率的にします。

モジュール、コンポーネントやサービスは*デコレーター*を使うクラスです。これらのデコレーターは型をマークしてAngularに用途を示すためのメタデータを提供します。

* コンポーネントクラスのメタデータは、それをビューを定義する *テンプレート* に関連付けます。テンプレートは通常のHTMLとAngular *ディレクティブ* と *バインディングマークアップ* を組み合わせています。これによりAngularは表示用にレンダリングする前にHTMLを変更できます。

* サービスクラスのメタデータは、*Dependency Injection（DI）* を通してサービスをコンポーネントで使用可能にするためにAngularが必要とする情報を提供します。

アプリケーションのコンポーネントは通常、階層的に配置された多数のビューを定義します。 Angularは、ビュー間のナビゲーションパスを定義するための`Router`サービスを提供します。ルーターは、高度なブラウザ内ナビゲーション機能を提供します。

<div class="alert is-helpful">

  重要なAngularの用語や使用法の基本的な定義については、 [Angular 用語集](guide/glossary) を参照してください。

</div>

<div class="alert is-helpful">

  For the sample app that this page describes, see the <live-example></live-example>.

</div>

## モジュール {@a modules}

Angularの*NgModule*はJavaScript（ES2015）のモジュールとは異なり、それを補完します。 
NgModuleは、アプリケーションドメイン、ワークフロー、あるいは一連の機能と密接に関連するコンポーネントセットのコンパイルコンテキストを宣言します。 
NgModuleは、そのコンポーネントをサービスなどの関連コードとまとめて、機能単位を形成できます。

すべてのAngularアプリケーションには、通常は`AppModule`という名前の *ルートモジュール* があり、アプリケーションを起動するブートストラップメカニズムを提供します。
アプリケーションには、通常、多くの機能モジュールが含まれています。

JavaScriptモジュールと同様に、NgModuleは他のNgModuleから機能をインポートし、独自の機能をエクスポートして他のNgModuleから使用できるようにします。
たとえば、アプリケーションでルーターのサービスを使用するには、`Router`のNgModuleをインポートします。

コードを個別の機能モジュールに整理することで、複雑なアプリケーションの開発を管理したり、再利用性を考慮した設計を行うのに役立ちます。
さらに、この技術を使用すると、起動時にロードする必要のあるコードの量を最小限に抑えるために、 *遅延ロード* 、&mdash;つまり要求に応じてモジュールをロードする&mdash;ことができます。

<div class="alert is-helpful">

  より詳細な議論については、[モジュールの概要](guide/architecture-modules)を参照してください。

</div>

## コンポーネント {@a components}

すべてのAngularアプリケーションには、少なくとも1つのコンポーネントがあります。その *ルートコンポーネント* は、コンポーネントの階層をページのドキュメントオブジェクトモデル (DOM)に接続します。各コンポーネントは、アプリケーションデータとロジックを含むクラスを定義し、ターゲット環境に表示されるビューを定義するHTML *テンプレート* に関連付けられます。

`@Component()`デコレーターは、そのすぐ下のクラスをコンポーネントとして識別し、テンプレートおよび関連するコンポーネント固有のメタデータを提供します。

<div class="alert is-helpful">

デコレーターは、JavaScriptクラスを変更する関数です。
Angularは、特定の種類のメタデータをクラスに付加する多数のデコレーターを定義しているため、システムはそれらのクラスが何を意味し、どのように動作するかを知ることができます。

<a href="https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841#.x5c2ndtx0">ウェブにおけるデコレーターの詳細を学びましょう。</a>

</div>

### テンプレート、ディレクティブ、およびデータバインディング

テンプレートはHTMLと、HTML要素を表示する前に変更できるAngularマークアップを組み合わせています。
テンプレート *ディレクティブ* はプログラムロジックを提供し、 *バインディングマークアップ* はアプリケーションデータとDOMを接続します。
データバインディングには2種類あります:

| Data bindings    | Details |
|:---              |:---     |
| イベントバインディング | アプリケーションデータを更新することで、ターゲット環境のユーザー入力に応答できます。|
| プロパティバインディング | アプリケーションデータから計算された値をHTMLに補間できます。|

ビューが表示される前に、Angularはディレクティブを評価し、テンプレートのバインディング構文を解決して、プログラムデータとロジックにしたがってHTML要素とDOMを変更します。 
Angularは *双方向データバインディング* をサポートしています。つまり、ユーザーの選択などDOMの変更をプログラムデータに反映させます。

テンプレートでは、 *パイプ* を使用して値を表示用に変換することで、ユーザー体験を向上させることもできます。
たとえば、日付と通貨の値をユーザーのロケールに適した方法で表示するためにパイプを使用します。 
Angularは一般的な変換用に事前定義されたパイプを提供し、さらに独自のパイプを定義することもできます。

<div class="alert is-helpful">

  これらの概念の詳細については、[コンポーネントの概要](guide/architecture-components)を参照してください。

</div>

<a id="dependency-injection"></a>

## サービスと依存オブジェクトの注入 {@a services-and-dependency-injection}

データやロジックが特定のビューに関連付けられておらず、かつコンポーネント間で共有したい場合は、 *サービス* クラスを作成します。 サービスクラスの定義は直前に`@Injectable()`デコレーターがあります。デコレーターは、他のプロバイダーを依存オブジェクトとしてクラスに *注入* するためのメタデータを提供します。

*Dependency Injection*（DI）を使用すると、コンポーネントクラスを無駄がなくかつ効率的な状態に保つことができます。コンポーネントがサーバーからデータを取得したり、ユーザーの入力を検証したり、コンソールに直接ログしたりすることはありません。そのようなタスクをサービスに委譲します。

<div class="alert is-helpful">

  詳細な議論については、[サービスとDIの紹介](guide/architecture-services)を参照してください。

</div>

### ルーティング

Angularの`Router` NgModuleは、アプリケーションのさまざまなアプリケーション状態とビュー階層の間でナビゲーションパスを定義できるサービスを提供します。これは使い慣れたブラウザのナビゲーションの規約に基づいています。

*   アドレスバーにURLを入力すると、ブラウザが対応するページに移動します。
*   ページ上のリンクをクリックすると、ブラウザが新しいページに移動します。
*   ブラウザの前後のボタンをクリックすると、ブラウザはあなたが見たページの履歴を前後にナビゲートします。

ルーターはURLのようなパスをページの代わりにビューにマップします。リンクのクリックなど、ユーザーが新しいページをブラウザでロードするアクションを実行すると、ルーターはブラウザの動作に介入し、ビュー階層を表示または非表示にします。

もし現在のアプリケーション状態に特定の機能が必要であり、それを定義するモジュールがロードされていないとルーターが判断した場合、ルーターは必要に応じてモジュールを *遅延ロード* できます。

ルーターは、あなたのアプリケーションのビューナビゲーションルールとデータの状態にしたがってリンクURLを解釈します。ユーザーがボタンをクリックしたり、ドロップボックスから選択したり、あるいは任意のソースからの他の刺激に応答したとき、新しいビューに移動できます。ルーターはブラウザの履歴にアクティビティを記録するので、戻るボタンと進むボタンも機能します。

ナビゲーションルールを定義するには、 *ナビゲーションパス* をコンポーネントに関連付けます。パスは、テンプレート構文がプログラムデータとビューを統合するのと同じ方法で、プログラムデータを統合するURLライクな構文を使用します。次に、プログラムロジックを適用して、ユーザーの入力と独自のアクセスルールに応じて、どのビューを表示または非表示にするかを選択できます。

 <div class="alert is-helpful">

詳細については、[ルーティングとナビゲーション](guide/router)を参照してください。

 </div>

## 次へ進む

Angularアプリケーションの主要な構成要素についての基礎を学びました。
次の図は、これらの基本パーツがどのように関連しているかを示しています。

<div class="lightbox">

<img alt="overview" src="generated/images/guide/architecture/overview2.png">

</div>

*   コンポーネントとテンプレートを合わせて、Angularのビューを定義します。
    *   コンポーネントクラスのデコレーターは、関連するテンプレートへの参照を含むメタデータを追加します。
    *   コンポーネントのテンプレート内のディレクティブとバインディングマークアップは、プログラムデータとロジックに基づいてビューを変更します。
*   依存性インジェクターは、サービスをコンポーネントに提供します。たとえばビュー間のナビゲーションを定義できるようにするルーターサービスなどです。

これらのテーマのそれぞれについては、次のページで詳しく説明します。

*   [モジュールの紹介](guide/architecture-modules)
*   [コンポーネントの紹介](guide/architecture-components)
    *   [テンプレートとビュー](guide/architecture-components#templates-and-views)
    *   [コンポーネントメタデータ](guide/architecture-components#component-metadata)
    *   [データバインディング](guide/architecture-components#data-binding)
    *   [ディレクティブ](guide/architecture-components#directives)
    *   [パイプ](guide/architecture-components#pipes)
*   [サービスと依存性の注入の紹介](guide/architecture-services)

これらの基本的な構成要素に精通していれば、ドキュメンテーションでもっと詳しく調べることができます。Angularアプリケーションの作成とデプロイに役立つツールやテクニックの詳細については、[次のステップ: ツールとテクニック](guide/architecture-next-steps)を参照してください。

</div>

<!-- links -->

<!-- external links -->

<!-- end links -->

@reviewed 2022-02-28
