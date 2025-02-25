---
title: Client.postMessage()
slug: Web/API/Client/postMessage
---

{{APIRef("Service Worker API")}}

**`postMessage()`** は {{domxref("Client")}} インターフェイスのメソッドで、サービスワーカーがクライアント ({{domxref("Window")}}, {{domxref("Worker")}}, {{domxref("SharedWorker")}}) にメッセージを送信することができます。 メッセージは、 {{domxref("ServiceWorkerContainer", "navigator.serviceWorker")}} の "`message`" イベントで受信されます。

## 構文

```
client.postMessage(message[, transfer]);
client.postMessage(message[, { transfer }]);
```

### 引数

- `message`
  - : クライアントに送信するメッセージです。これは、任意の[複製可能な構造化型](/ja/docs/Web/API/Web_Workers_API/Structured_clone_algorithm)にすることができます。
- `transfer` {{optional_inline}}
  - : メッセージとともに[転送](/ja/docs/Web/API/Transferable)されるオブジェクトのシーケンスです。 これらのオブジェクトの所有権は宛先側に与えられ、送信側では使用できなくなります。

### 返値

`undefined`。

## 例

サービスワーカーからクライアントへのメッセージの送信

```js
addEventListener('fetch', event => {
  event.waitUntil(async function() {
    // クライアントにアクセスできない場合は、早期に終了します。
    // 例えば、クロスオリジンの場合。
    if (!event.clientId) return;

    // クライアントを取得します。
    const client = await clients.get(event.clientId);
    // クライアントを取得できない場合は、早期に終了します。
    // 例えば、閉じている場合。
    if (!client) return;

    // クライアントにメッセージを送信します。
    client.postMessage({
      msg: "私はあなたからフェッチされましたよ！",
      url: event.request.url
    });

  }());
});
```

そのメッセージの受け取り

```js
navigator.serviceWorker.addEventListener('message', event => {
  console.log(event.data.msg, event.data.url);
});
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat("api.Client.postMessage")}}
