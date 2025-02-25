---
title: IDBDatabase
slug: Web/API/IDBDatabase
---

{{APIRef()}}

IndexedDB API の `IDBDatabase` インターフェイスは、[データベースへの接続](/ja/docs/IndexedDB#database_connection)を提供します。`IDBDatabase` オブジェクトで、データベースの[トランザクション](/ja/docs/IndexedDB#gloss_transaction)を開き、データベースのオブジェクト（データ）を生成したり、操作したり、削除したりできます。このインターフェイスはデータベースのバージョンを取得したり、統合したりする唯一の方法を提供します。

> **メモ:** IndexedDB 内で行う全ての操作は、データベース内のデータとの作用を表す[トランザクション](/ja/docs/IndexedDB/Basic_Concepts_Behind_IndexedDB#gloss_transaction)の文脈で起こります。IndexedDB 内の全てのオブジェクト (オブジェクトストア、インデックス、カーソルを含みます) は、特定のトランザクションに紐づいています。そのため、トランザクション外では、コマンドを実行したり、データにアクセスしたり、何かを開いたりできません。

## インスタンスメソッド

[EventTarget](/ja/docs/DOM/EventTarget) から継承します。

- {{domxref("IDBDatabase.close")}}
  - : 即座に応答して、別スレッドでデータベースを閉じます。
- {{domxref("IDBDatabase.createObjectStore")}}
  - : 新しくオブジェクトストアかインデックスを生成して返します。
- {{domxref("IDBDatabase.deleteObjectStore")}}
  - : 参照しているインデックスがあったとしても、接続中のデータベースで与えられた名前のオブジェクトストアを削除します。
- {{domxref("IDBDatabase.transaction")}}
  - : オブジェクトストアにアクセスできる{{domxref("IDBTransaction.objectStore")}}メソッドを含むトランザクションオブジェクト ({{domxref("IDBTransaction")}})を即座に返します。別スレッドで実行されます。

## インスタンスプロパティ

- {{domxref("IDBDatabase.name")}} {{readonlyInline}}
  - : 接続しているデータベース名を含む{{ domxref("DOMString") }}。
- {{domxref("IDBDatabase.version")}} {{readonlyInline}}
  - : 接続しているデータベースのバージョンを含む [64-bit integer](</ja/docs/NSPR_API_Reference/Long_Long_(64-bit)_Integers>)。データベースが初めて作られた場合、この属性は空文字です。
- {{domxref("IDBDatabase.objectStoreNames")}} {{readonlyInline}}
  - : 接続しているデータベースの[オブジェクトストア](/ja/docs/IndexedDB#gloss_object_store)名のリストを含む{{ domxref("DOMStringList") }}。

### イベント

- {{domxref("IDBDatabase.onabort")}}
  - : データベースの接続が中止された場合に発生します。
- {{domxref("IDBDatabase.onerror")}}
  - : データベースへの接続が失敗した場合に発生します。
- {{domxref("IDBDatabase.onversionchange")}}
  - : データベースの構造が {{domxref("IDBOpenDBRequest.onupgradeneeded")}} イベントで変更されるか、{{domxref("IDBFactory.deleteDatabase")}} がどこかで (ほとんどの場合、同じコンピューターの他のウィンドウやタブで) 要求された場合に発生します。これは version change transaction ({{domxref("IDBVersionChangeEvent")}} を参照) とは異なりますが、関連があります。

## 例

次のコードスニペットでは、データベースを非同期で開き ({{domxref("IDBFactory")}})、成功と失敗の場合にイベントを登録し、アップグレードが必要な場合には、新しいオブジェクトストアを生成しています ({{ domxref("IDBdatabase") }})。 完璧に動作する例は、[To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) アプリケーション ([動く例を見る](https://mdn.github.io/dom-examples/to-do-notifications/)) を見てください。

```js
// 我々のデータベースを開きましょう
  var DBOpenRequest = window.indexedDB.open("toDoList", 4);


  // これら 2 個のイベントハンドラーは､データベースが正常に開かれたか､失敗した時に動作します｡
  DBOpenRequest.onerror = function(event) {
    note.innerHTML += '<li>データベースの読み込みに失敗しました｡</li>';
  };

  DBOpenRequest.onsuccess = function(event) {
    note.innerHTML += '<li>データベースを初期化しました｡</li>';

    // データベースを開いた結果を変数 db に保存します｡これは後でたくさん使います｡
    db = DBOpenRequest.result;

    // displayData() 関数を実行し、タスクリストに既に IDB にある全ての to-do リストデータを入れます。
    displayData();
  };

  // このイベントハンドラーは、新しいバージョンのデータベースの作成が必要なことを表すイベントを処理します。
  // これは、データベースが作成されていないときや、上の行の window.indexedDB.open に
  // 新しいバージョン番号が渡されたときです。

  DBOpenRequest.onupgradeneeded = function(event) {
    var db = event.target.result;

    db.onerror = function(event) {
      note.innerHTML += '<li>データベースの読み込みに失敗しました｡</li>';
    };

    // IDBDatabase.createObjectStore を用いてデータベースにオブジェクトストアを作成します。

    var objectStore = db.createObjectStore("toDoList", { keyPath: "taskTitle" });

    // オブジェクトストアにどのようなデータ項目が入るかを定義します。

    objectStore.createIndex("hours", "hours", { unique: false });
    objectStore.createIndex("minutes", "minutes", { unique: false });
    objectStore.createIndex("day", "day", { unique: false });
    objectStore.createIndex("month", "month", { unique: false });
    objectStore.createIndex("year", "year", { unique: false });

    objectStore.createIndex("notified", "notified", { unique: false });

    note.innerHTML += '<li>オブジェクトストアが作成されました。</li>';
  };
```

次の行は、データベースでトランザクションを開いて、そしてオブジェクトストアを開いて、内側のデータを操作しています。

```js
    var objectStore = db.transaction('toDoList').objectStore('toDoList');
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat("api.IDBDatabase")}}

## 関連情報

- [IndexedDB の使用](/ja/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- トランザクションの開始 : {{domxref("IDBDatabase")}}
- トランザクションの使用 : {{domxref("IDBTransaction")}}
- キーの範囲の設定 : {{domxref("IDBKeyRange")}}
- データの取得と変更 : {{domxref("IDBObjectStore")}}
- カーソルの使用 : {{domxref("IDBCursor")}}
- リファレンス例 : [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([動く例を見る](https://mdn.github.io/dom-examples/to-do-notifications/))
