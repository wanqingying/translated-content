---
title: HTMLMediaElement
slug: Web/API/HTMLMediaElement
---

{{APIRef("HTML DOM")}}

**`HTMLMediaElement`** インターフェイスは {{domxref("HTMLElement")}} に音声や動画で一般的なメディアに関する基本的な能力の対応に必要なプロパティやメソッドを追加します。

{{domxref("HTMLVideoElement")}} および {{domxref("HTMLAudioElement")}} 要素はどちらも、このインターフェイスを継承しています。

{{InheritanceDiagram}}

## プロパティ

_このインターフェイスは祖先である {{domxref("HTMLElement")}}, {{domxref("Element")}}, {{domxref("Node")}}, {{domxref("EventTarget")}} のプロパティを継承しています。_

- {{domxref("HTMLMediaElement.audioTracks")}}
  - : {{domxref("AudioTrackList")}} で、この要素に含まれる {{domxref("AudioTrack")}} オブジェクトを列挙します。
- {{domxref("HTMLMediaElement.autoplay")}}

  - : 論理値で、 HTML の {{htmlattrxref("autoplay", "video")}} 属性の値を反映し、中断なしに再生できるだけの十分なデータが揃った時点で自動的に再生を始めるかどうかを示します。

    > **メモ:** ユーザーが期待していない、あるいは望んでいないときに自動的に音声を再生すると、ユーザーに不快な体験をさせることになるため、ほとんどの場合避けるべきですが、例外も存在します。詳しくは、[メディアとウェブオーディオ API のガイド](/ja/docs/Web/Media/Autoplay_guide)を参照してください。ブラウザーは自動再生要求を無視する可能性があることを念頭に置き、コードが自動再生の動作に依存していないことを確認する必要があります。

- {{domxref("HTMLMediaElement.buffered")}} {{readonlyinline}}
  - : `buffered` プロパティにアクセスした時点で、ブラウザーがバッファリングしているメディアソースの範囲を（もしあれば） {{domxref("TimeRanges")}} オブジェクトで返します。
- {{domxref("HTMLMediaElement.controls")}}
  - : 論理値で、 HTML の {{htmlattrxref("controls", "video")}} 属性を反映し、リソースを制御するユーザーインターフェイス項目を表示するかどうかを示します。
- {{domxref("HTMLMediaElement.controlsList")}} {{readonlyinline}}
  - : ユーザーエージェントが独自のコントロールのセットを表示するたびに、メディア要素に表示するコントロールをユーザーエージェントが選択するのに役立つ {{domxref("DOMTokenList")}} を返します。 `DOMTokenList`は、`nodownload`、`nofullscreen`、`noremoteplayback`の3つの値のうち 1 つ以上を取ります。
- {{domxref("HTMLMediaElement.crossOrigin")}}
  - : 文字列で、このメディア要素の [CORS 設定](/ja/docs/Web/HTML/Attributes/crossorigin)を示します。
- {{domxref("HTMLMediaElement.currentSrc")}}{{readonlyinline}}
  - : 文字列で、選択されたメディアリソースの絶対 URL を返します。
- {{domxref("HTMLMediaElement.currentTime")}}
  - : 倍精度浮動小数点値で、現在の再生時刻を秒単位で示します。メディアの再生が開始されておらず、シークも行われていない場合、この値はメディアの初期再生時刻となります。この値を設定すると、メディアは新しい時刻にシークされます。この時間は、メディアのタイムラインに対して相対的に指定されます。
- {{domxref("HTMLMediaElement.defaultMuted")}}
  - : 論理値で、HTML の {{htmlattrxref("muted", "video")}} 属性を反映します。標準状態で音声がミュートされているか、いないかを示します。
- {{domxref("HTMLMediaElement.defaultPlaybackRate")}}
  - : `double` で、メディアの既定の再生速度を示します。
- {{domxref("HTMLMediaElement.disableRemotePlayback")}}
  - : 論理値で、リモート再生の状態を設定または返却します。メディア要素にリモート再生 UI が許可されているかどうかを示します。
- {{domxref("HTMLMediaElement.duration")}} {{readonlyinline}}
  - : 読み取り専用の倍精度浮動小数点値で、メディアの総時間を秒単位で示します。メディアデータがない場合、返値は `NaN` となります。メディアの長さが不定 （ライブストリーミングメディアや WebRTC 呼び出しのメディアなど）の場合、 値は `+Infinity` となります。
- {{domxref("HTMLMediaElement.ended")}} {{readonlyinline}}
  - : メディア要素の再生が終了したかどうかを示す論理値を返します。
- {{domxref("HTMLMediaElement.error")}} {{readonlyinline}}
  - : 直近のエラーに対応する {{domxref("MediaError")}} オブジェクトを返すか、エラーが発生していない場合は `null` を返します。
- {{domxref("HTMLMediaElement.loop")}}
  - : 論理型で、 HTML の {{htmlattrxref("loop", "video")}} 属性を反映し、末尾に達したときにメディア要素が再び再生を始めるかどうかを示します。
- {{domxref("HTMLMediaElement.mediaKeys")}} {{readonlyinline}} {{experimental_inline}}
  - : {{domxref("MediaKeys")}} オブジェクトまたは `null` を返します。 MediaKeys は、関連付けられた HTMLMediaElement が再生中にメディアデータの復号に使用できるキーのセットです。
- {{domxref("HTMLMediaElement.muted")}}
  - : 音声がミュートされているかどうかを判断するための論理値です。ミュートされている場合は `true` で、そうでない場合は `false` となります。
- {{domxref("HTMLMediaElement.networkState")}} {{readonlyinline}}
  - : ネットワーク経由でメディアを取得する際の現在の状態を示す `unsigned short` （列挙値）を返します。
- {{domxref("HTMLMediaElement.paused")}} {{readonlyinline}}
  - : 論理値で、メディア要素が一時停止中であるか否かを示します。
- {{domxref("HTMLMediaElement.playbackRate")}}
  - : `double` で、メディアの再生レートを示します。
- {{domxref("HTMLMediaElement.played")}} {{readonlyinline}}
  - : ブラウザーが再生したメディアソースの範囲を含む {{domxref('TimeRanges')}} オブジェクトを返します（もしあれば）。
- {{domxref("HTMLMediaElement.preload")}}
  - : HTML の {{htmlattrxref("preload", "video")}} 属性を反映した文字列で、どのデータを先読みすべきかを示します。指定可能な値は `none`, `metadata`, `auto` です。
- {{domxref("HTMLMediaElement.preservesPitch")}}
  - : 音のピッチを保持するかどうかを決定する論理値です。 `false` に設定すると、ピッチは音声の速度に合わせられます。
- {{domxref("HTMLMediaElement.readyState")}} {{readonlyinline}}
  - : メディアの準備状態を示す `unsigned short` （列挙値）を返します。
- {{domxref("HTMLMediaElement.seekable")}} {{readonlyinline}}
  - : ユーザーがシークできる時間帯があれば、それを含む {{domxref('TimeRanges')}} オブジェクトを返します。
- {{domxref("HTMLMediaElement.seeking")}} {{readonlyinline}}
  - : メディアが新しい位置へのシーク中であるかどうかを論理値で返します。
- {{domxref("HTMLMediaElement.sinkId")}} {{readonlyinline}} {{experimental_inline}}
  - : 出力を配信する音声機器の一意の ID を文字列で返します。ユーザーエージェントの既定値を使用している場合は、空の文字列を返します。この ID は {{domxref("MediaDevices.enumerateDevices()")}} から返される `MediaDeviceInfo.deviceid` 値、 `id-multimedia` 値、 `id-communications` 値のいずれかである必要があります。
- {{domxref("HTMLMediaElement.src")}}
  - : 使用するメディアリソースの URL を記した HTML の {{htmlattrxref("src", "video")}} 属性を反映した文字列です。
- {{domxref("HTMLMediaElement.srcObject")}}
  - : 現在の `HTMLMediaElement` で再生する、または再生したメディアを表す {{domxref('MediaStream')}}、または割り当てられていない場合は `null` です。
- {{domxref("HTMLMediaElement.textTracks")}} {{readonlyinline}}
  - : {{domxref('TextTrackList')}} オブジェクトで、この要素に含まれる {{domxref("TextTrack")}} オブジェクトのリストを返します。
- {{domxref("HTMLMediaElement.videoTracks")}} {{readonlyinline}}
  - : {{domxref('VideoTrackList')}} オブジェクトで、この要素に含まれる {{domxref("VideoTrack")}} オブジェクトのリストを返します。
- {{domxref("HTMLMediaElement.volume")}}
  - : `double` で音声の音量を示します。 0.0 (無音) から 1.0 (最大) の間です。

### イベントハンドラー

- {{domxref("HTMLMediaElement.onencrypted")}}
  - : メディアが暗号化されたときに呼び出されるイベントハンドラーを設定します。
- {{domxref("HTMLMediaElement.onwaitingforkey")}}
  - : 暗号化キー待ちで再生がブロックされたときに呼び出されるイベントハンドラーを設定します。

## 廃止されたプロパティ

これらのプロパティは廃止されており、たとえブラウザーがまだ対応していても使わないでください。

- {{domxref("HTMLMediaElement.controller")}} {{deprecated_inline}}
  - : 要素に割り当てられたメディアコントローラーを表す {{domxref("MediaController")}} オブジェクト、または何も割り当てられていない場合は `null` です。
- {{domxref("HTMLMediaElement.mediaGroup")}} {{deprecated_inline}}
  - : 所属する要素のグループ名を示す HTML の {{ htmlattrxref("mediagroup", "video")}} 属性を反映した文字列です。メディア要素のグループは、共通の {{domxref('MediaController')}} を共有します。
- {{domxref("HTMLMediaElement.mozAudioCaptured")}} {{readonlyinline}} {{non-standard_inline}} {{deprecated_inline}}
  - : 論理値を返します。オーディオストリームキャプチャに関連する項目です。
- {{domxref("HTMLMediaElement.mozFragmentEnd")}} {{non-standard_inline}} {{deprecated_inline}}
  - : `double` で、メディア要素が `currentSrc` のフラグメント URI を持っている場合はフラグメントの終了時刻にアクセスすることができます。それ以外の場合はメディアの再生時間と同じです。

## メソッド

_このインターフェイスには祖先である {{domxref("HTMLElement")}}, {{domxref("Element")}}, {{domxref("Node")}}, {{domxref("EventTarget")}} から継承したメソッドもあります。_

- {{domxref("HTMLMediaElement.addTextTrack()")}}
  - : メディア要素に新しい {{domxref("TextTrack")}} オブジェクト（字幕用トラックなど）を追加します。これはプログラム的なインターフェイスのみで、 DOM には影響しません。
- {{domxref("HTMLMediaElement.captureStream()")}} {{experimental_inline}}
  - : メディアコンテンツのストリームをキャプチャして {{domxref("MediaStream")}} 返します。
- {{domxref("HTMLMediaElement.canPlayType()")}}
  - : MIME メディア種別を指定する文字列（潜在的には [`codecs` 引数](/ja/docs/Web/Media/Formats/codecs_parameter)も含む）が与えられた場合、 `canPlayType()` は、メディアが再生可能であるべき場合には文字列 `probably` を、メディアが再生されるかどうかを決定するのに十分な情報がない場合には `maybe` を、メディアが再生できない場合には空文字列を返します。
- {{domxref("HTMLMediaElement.fastSeek()")}}
  - : 低い精度で素早く指定時刻にシークします。
- {{domxref("HTMLMediaElement.load()")}}
  - : メディア要素をリセットし、メディアリソースをリスタートします。処理されなかったイベントは破棄されます。メディアデータがダウンロードされる量は `preload` 属性の値に影響されます。`src` 属性の値、もしくは `source` 要素内の要素を削除した際のリソース解放、もしくは `source` の子要素が動的に変更される場合の再スキャンのために利用します。それ以外の場合に呼びだす必要はありません。
- {{domxref("HTMLMediaElement.pause()")}}
  - : 再生を一時停止します。
- {{domxref("HTMLMediaElement.play()")}}
  - : 再生を開始します。
- {{domxref("HTMLMediaElement.seekToNextFrame()")}} {{non-standard_inline}} {{experimental_inline}} {{deprecated_inline}}
  - : メディア内の次のフレームをシークします。この非標準的で実験的なメソッドにより、メディアの読み込みとレンダリングをカスタム速度で手動で行ったり、メディアをフレーム単位で移動してフィルタリングやその他の操作を行ったりすることが可能になります。
- {{domxref("HTMLMediaElement.setMediaKeys()")}} {{experimental_inline}}
  - : 再生に利用する{{domxref("MediaKeys")}} を指定します。{{jsxref("Promise")}} オブジェクトを返します。
- {{domxref("HTMLMediaElement.setSinkId()")}} {{experimental_inline}}
  - : 出力に使用するオーディオ機器の ID を設定し、{{jsxref("Promise")}} を返します。これは、アプリケーションが指定された機器の使用が許可されている場合のみ動作します。

## 廃止されたメソッド

_これらのメソッドは廃止されているため、たとえブラウザーがまだ対応していても使わないでください。_

- {{domxref("HTMLMediaElement.mozCaptureStream()")}} {{non-standard_inline}}
  - : \[説明を入力]
- {{domxref("HTMLMediaElement.mozCaptureStreamUntilEnded()")}} {{non-standard_inline}} {{deprecated_inline}}
  - : \[説明を入力]
- {{domxref("HTMLMediaElement.mozGetMetadata()")}} {{non-standard_inline}}
  - : 再生中のメディアデータに対するメタデータを {{jsxref('Object')}} として返します。呼び出すたびに、オブジェクトのコピーが新しく作られます。このメソッドを呼び出すには、[loadedmetadata](/ja/docs/Web/API/HTMLMediaElement/loadedmetadata_event) イベントが発行された後でなければなりません。

## イベント

_親である {{domxref("HTMLElement")}}_ や、 {{domxref('GlobalEventHandlers')}} ミックスインから継承したメソッドがあります。これらのイベントを待ち受けするには、 [`addEventListener()`](/ja/docs/Web/API/EventTarget/addEventListener) を使用するか、このインターフェイスの `onイベント名` プロパティにイベントリスナーを代入するかしてください。

- {{domxref("HTMLMediaElement.abort_event", 'abort')}}
  - : リソースが完全にロードされておらず、かつその結果がエラーでない場合に発行されます。
- {{domxref("HTMLMediaElement.canplay_event", 'canplay')}}
  - : ユーザーエージェントがメディアを再生することはできるが、コンテンツのさらなるバッファリングのために停止することなくメディアを最後まで再生するには十分なデータが読み込まれて**いない**と推定されるときに発行されます。
- {{domxref("HTMLMediaElement.canplaythrough_event", 'canplaythrough')}}
  - : ユーザーエージェントがメディアを再生することができ、コンテンツのさらなるバッファリングのために停止することなく、メディアを最後まで再生するのに十分なデータが読み込まれたと推定されるときに発行されます。
- {{domxref("HTMLMediaElement.durationchange_event", 'durationchange')}}
  - : duration プロパティが更新されたときに発行されます。
- {{domxref("HTMLMediaElement.emptied_event", 'emptied')}}
  - : メディアが空になったときに発行されます。例えば、メディアがすでに読み込まれており（または部分的に読み込まれており）、再読み込みのために {{domxref("HTMLMediaElement.load()")}} メソッドが呼ばれた場合などです。
- {{domxref("HTMLMediaElement.ended_event", 'ended')}}
  - : メディア（\<audio> または \<video>）の終端に到達したとき、またはそれ以降のデータがないために再生が停止したときに発行されます。
- {{domxref("HTMLMediaElement.error_event", 'error')}}
  - : エラーによりリソースの読み込みができなかった場合に発行されます。
- {{domxref("HTMLMediaElement.loadeddata_event", 'loadeddata')}}
  - : メディアの 1 フレーム目の読み込みが終了した時点で発行されます。
- {{domxref("HTMLMediaElement.loadedmetadata_event", 'loadedmetadata')}}
  - : メタデータが読み込まれたときに発行されます。
- {{domxref("HTMLMediaElement.loadstart_event", 'loadstart')}}
  - : ブラウザーがリソースの読み込みを開始したときに発行されます。
- {{domxref("HTMLMediaElement.pause_event", 'pause')}}
  - : 再生を一時停止する要求が処理され、アクティビティが一時停止状態になったときに発行されます。最も一般的には、メディアの {{domxref("HTMLMediaElement.pause()")}} メソッドが呼び出されたときに発行されます。
- {{domxref("HTMLMediaElement.play_event", 'play')}}
  - : {{domxref("HTMLMediaElement.play()")}} メソッド、または `autoplay` 属性の結果として、 `paused` プロパティが `true` から `false` に変更されたときに発行されます。
- {{domxref("HTMLMediaElement.playing_event", "playing")}}
  - : データ不足で一時停止または遅延していた再生が開始できる状態になったときに発行されます。
- {{domxref("HTMLMediaElement.progress_event", "progress")}}
  - : ブラウザーがリソースを読み込む際に、定期的に発行されます。
- {{domxref("HTMLMediaElement.ratechange_event", 'ratechange')}}
  - : 再生速度が変更されたときに発行されます。
- {{domxref("HTMLMediaElement.resize_event", 'resize ')}}
  - : `videoWidth` および `videoHeight` プロパティの一方または両方が更新された直後に発行されます。
- {{domxref("HTMLMediaElement.seeked_event", 'seeked ')}}
  - : シーク動作が完了したときに発行されます。
- {{domxref("HTMLMediaElement.seeking_event", 'seeking')}}
  - : シーク動作が開始されたときに発行されます。
- {{domxref("HTMLMediaElement.stalled_event", 'stalled')}}
  - : ユーザーエージェントがメディアデータを取得しようとしたが，予想に反してデータが得られなかった場合に発行されます。
- {{domxref("HTMLMediaElement.suspend_event", 'suspend')}}
  - : メディアデータの読み込みが中断されたときに発行されます。
- {{domxref("HTMLMediaElement.timeupdate_event", 'timeupdate')}}
  - : {{domxref("HTMLMediaElement.currentTime", "currentTime")}} プロパティで示される時刻が更新されたときに発行されます。
- {{domxref("HTMLMediaElement.volumechange_event", 'volumechange')}}
  - : 音量が変更されたときに発行されます。
- {{domxref("HTMLMediaElement.waiting_event", 'waiting')}}
  - : 一時的なデータ不足で再生が停止したときに発行されます。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

### リファレンス

- HTML の {{HTMLElement("video")}} および {{HTMLElement("audio")}} 要素
- `HTMLMediaElement` を継承している {{domxref("HTMLVideoElement")}} および {{domxref("HTMLAudioElement")}} インターフェイス

### ガイド

- [ウェブメディア技術](/ja/docs/Web/Media)
- 学習領域: [動画および音声コンテンツ](/ja/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)
- [ウェブ上のメディア型と形式のガイド](/ja/docs/Web/Media/Formats)
- [ウェブコンテンツにおけるメディア対応の問題の扱い](/ja/docs/Web/Media/Formats/Support_issues)
