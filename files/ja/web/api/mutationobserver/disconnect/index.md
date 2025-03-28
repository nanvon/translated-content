---
title: MutationObserver.disconnect()
slug: Web/API/MutationObserver/disconnect
---
{{APIRef("DOM WHATWG")}}

{{domxref("MutationObserver")}} の **`disconnect()`** メソッドは、オブザーバーに変更の監視を停止させます。 オブザーバーは、 {{domxref("MutationObserver.observe", "observe()")}} メソッドを再度呼び出すことで再利用できます。

## 構文

```
mutationObserver.disconnect()
```

### 引数

なし

### 戻り値

`undefined`

> **Note:** **注:** すでに検知されているものの、まだオブザーバーに報告されていない変更の通知は、すべて破棄されます。

## 使用における注意点

監視されている要素が DOM から削除され、その後ブラウザのガベージコレクション機構によって解放された場合、`MutationObserver` も同様に削除されます。

## 例

この例では、オブザーバを作成してから切断し、再利用できるようにします。

```js
const targetNode = document.querySelector("#someElement");
const observerOptions = {
  childList: true,
  attributes: true
}

const observer = new MutationObserver(callback);
observer.observe(targetNode, observerOptions);

/* some time later... */

observer.disconnect();
```

## 仕様

| Specification                                                                                                                    | Status                           | Comment |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- | ------- |
| {{SpecName('DOM WHATWG', '#dom-mutationobserver-disconnect', 'MutationObserver.disconnect()')}} | {{ Spec2('DOM WHATWG') }} |         |

## ブラウザ互換性

{{Compat("api.MutationObserver.disconnect")}}
