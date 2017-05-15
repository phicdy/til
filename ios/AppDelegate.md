
* デフォルトではAppDelegate.swiftにAppDelegateクラスとして宣言される
* アプリのコンテンツが描かれるウィンドウと状態変更に応答する場所を提供する
* @UIApplicationMainを付けることでアプリのエントリーポイントとなり、ループを作る
* @UIApplicationMainはUIApplicationMainの機能を呼び、AppDelegateのクラス名をdelegateクラスとして結びつける
* そのレスポンス内でapplicationオブジェクトを作る。これはアプリのライフサイクルを管理する。
* システムはAppDelegateクラスのインスタンスを作り、そのapplicationオブジェクトにアサインする
* 最後にシステムはアプリを立ち上げる
* プロジェクト作成時にAppDelegateは自動的に作られ、UIApplicationDelegateプロトコルが適用される。このプロトコルはアプリの状態変更時の設定と、アプリレベルのイベントをハンドリングするためのメソッドを提供する

https://developer.apple.com/library/content/referencelibrary/GettingStarted/DevelopiOSAppsSwift/BuildABasicUI.html