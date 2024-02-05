---
title: "Flutter ListView内でTextFieldを使用する際の注意点"
emoji: "🍣"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["flutter"]
published: true
---
Flutterで個人開発中にListViewの中でTextFieldを使用したい場面があったので実装したところ、以下のようなレンダリングエラーが出たため備忘録として記録しておきます。

## エラー
````
======== Exception caught by rendering library =====================================================
The following assertion was thrown during paint():
RenderBox was not laid out: RenderRepaintBoundary#6f538 NEEDS-LAYOUT NEEDS-PAINT
'package:flutter/src/rendering/box.dart':
Failed assertion: line 1972 pos 12: 'hasSize'


Either the assertion indicates an error in the framework itself, or we should provide substantially more information in this error message to help you determine and fix the underlying cause.
In either case, please report this assertion by filing a bug on GitHub:
  https://github.com/flutter/flutter/issues/new?template=2_bug.yml

The relevant error-causing widget was: 
  TextField TextField:file:///C:/Users/kite0/StudioProjects/counter/lib/list_page.dart:37:27
When the exception was thrown, this was the stack: 
#2      RenderBox.size (package:flutter/src/rendering/box.dart:1972:12)
#3      RenderBox.paintBounds (package:flutter/src/rendering/box.dart:2636:41)
#4      PaintingContext._repaintCompositedChild (package:flutter/src/rendering/object.dart:165:56)
#5      PaintingContext.repaintCompositedChild (package:flutter/src/rendering/object.dart:109:5)
#6      PaintingContext._compositeChild (package:flutter/src/rendering/object.dart:261:7)
#7      PaintingContext.paintChild (package:flutter/src/rendering/object.dart:242:7)
#8      _RenderDecoration.paint.doPaint (package:flutter/src/material/input_decorator.dart:1552:17)
#9      _RenderDecoration.paint (package:flutter/src/material/input_decorator.dart:1614:5)
#10     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#11     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#12     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#13     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#14     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#15     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#16     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#17     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#18     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#19     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#20     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#21     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#22     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#23     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#24     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#25     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#26     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#27     RenderBoxContainerDefaultsMixin.defaultPaint (package:flutter/src/rendering/box.dart:2882:15)
#28     RenderFlex.paint (package:flutter/src/rendering/flex.dart:1040:7)
#29     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#30     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#31     RenderShiftedBox.paint (package:flutter/src/rendering/shifted_box.dart:74:15)
#32     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#33     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#34     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#35     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#36     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#37     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#38     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#39     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#40     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#41     _RenderInkFeatures.paint (package:flutter/src/material/material.dart:662:11)
#42     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#43     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#44     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#45     RenderCustomPaint.paint (package:flutter/src/rendering/custom_paint.dart:633:11)
#46     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#47     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#48     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#49     RenderPhysicalShape.paint.<anonymous closure> (package:flutter/src/rendering/proxy_box.dart:2156:15)
#50     PaintingContext.pushClipPath (package:flutter/src/rendering/object.dart:614:14)
#51     RenderPhysicalShape.paint (package:flutter/src/rendering/proxy_box.dart:2143:21)
#52     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#53     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#54     RenderShiftedBox.paint (package:flutter/src/rendering/shifted_box.dart:74:15)
#55     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#56     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#57     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#58     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#59     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#60     RenderShiftedBox.paint (package:flutter/src/rendering/shifted_box.dart:74:15)
#61     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#62     PaintingContext.paintChild (package:flutter/src/rendering/object.dart:250:13)
#63     RenderProxyBoxMixin.paint (package:flutter/src/rendering/proxy_box.dart:129:13)
#64     RenderObject._paintWithContext (package:flutter/src/rendering/object.dart:3208:7)
#65     PaintingContext._repaintCompositedChild (package:flutter/src/rendering/object.dart:166:11)
#66     PaintingContext.repaintCompositedChild (package:flutter/src/rendering/object.dart:109:5)
#67     PipelineOwner.flushPaint (package:flutter/src/rendering/object.dart:1156:31)
#68     PipelineOwner.flushPaint (package:flutter/src/rendering/object.dart:1166:15)
#69     RendererBinding.drawFrame (package:flutter/src/rendering/binding.dart:593:23)
#70     WidgetsBinding.drawFrame (package:flutter/src/widgets/binding.dart:986:13)
#71     RendererBinding._handlePersistentFrameCallback (package:flutter/src/rendering/binding.dart:457:5)
#72     SchedulerBinding._invokeFrameCallback (package:flutter/src/scheduler/binding.dart:1325:15)
#73     SchedulerBinding.handleDrawFrame (package:flutter/src/scheduler/binding.dart:1255:9)
#74     SchedulerBinding.scheduleWarmUpFrame.<anonymous closure> (package:flutter/src/scheduler/binding.dart:978:7)
#78     _RawReceivePort._handleMessage (dart:isolate-patch/isolate_patch.dart:184:12)
(elided 5 frames from class _AssertionError, class _Timer, and dart:async-patch)
The following RenderObject was being processed when the exception was fired: _RenderDecoration#aba73 relayoutBoundary=up7
...  needs compositing
...  parentData: <none> (can use size)
...  constraints: BoxConstraints(0.0<=w<=Infinity, 0.0<=h<=100.0)
...  size: MISSING
RenderObject: _RenderDecoration#aba73 relayoutBoundary=up7
  needs compositing
  parentData: <none> (can use size)
  constraints: BoxConstraints(0.0<=w<=Infinity, 0.0<=h<=100.0)
  size: MISSING
...  input: RenderRepaintBoundary#6f538 NEEDS-LAYOUT NEEDS-PAINT
...    needs compositing
...    parentData: offset=Offset(0.0, 0.0)
...    constraints: MISSING
...    layer: OffsetLayer#d9510 DETACHED
...      handles: 1
...      offset: Offset(0.0, 0.0)
...    size: MISSING
...    metrics: 0.0% useful (1 bad vs 0 good)
...    diagnosis: insufficient data to draw conclusion (less than five repaints)
...    child: _RenderCompositionCallback#400d3 NEEDS-LAYOUT NEEDS-PAINT
...      needs compositing
...      parentData: <none>
...      constraints: MISSING
...      size: MISSING
...      child: RenderTapRegion#50d0c NEEDS-LAYOUT NEEDS-PAINT
...        needs compositing
...        parentData: <none>
...        constraints: MISSING
...        size: MISSING
...        behavior: deferToChild
...        debugLabel: EditableText
...        groupId: EditableText
...        child: RenderMouseRegion#328cc NEEDS-LAYOUT NEEDS-PAINT
...          needs compositing
...          parentData: <none>
...          constraints: MISSING
...          size: MISSING
...          behavior: opaque
...          listeners: <none>
...  helperError: RenderConstrainedBox#3ae28 NEEDS-LAYOUT NEEDS-PAINT
...    parentData: offset=Offset(0.0, 0.0)
...    constraints: MISSING
...    size: MISSING
...    additionalConstraints: BoxConstraints(w=0.0, h=0.0)
...  container: RenderCustomPaint#1fe97 NEEDS-LAYOUT NEEDS-PAINT
...    parentData: offset=Offset(0.0, 0.0)
...    constraints: MISSING
...    size: MISSING
...    painter: null
...    foregroundPainter: _InputBorderPainter#0cea8
====================================================================================================
````

### (コード修正前)
````dart
body: Center(
        child: Container(
          child: ListView.builder(
            itemCount: value,
            itemBuilder: (context, index) {
              // ListItemDateからデータを取得
              String alphabet = ListItemData().alphabets[index];
              return Center(
                child: Card(
                  child: SizedBox(
                    width: double.infinity,
                    height: 100,
                    child: Center(
                      child: Row(
                        children: [
                          Expanded(
                            child: Container(
                              color: Colors.blue,
                              child: Text(alphabet),
                            ),
                          ),
                          TextField(),
                          Row(
                            children: [
                              Container(
                                color: Colors.red,
                                child: ElevatedButton(
                                  onPressed: () {},
                                  child: Text('追加'),
                                ),
                              ),
                              Container(
                                color: Colors.red,
                                child: ElevatedButton(
                                  onPressed: () {},
                                  child: Text('削除'),
                                ),
                              ),
                            ],
                          ),
                        ],
                      ),
                    ),
                  ),
                ),
              );
            },
          ),
        ),
      ),
````
エラーの内容を大まかにまとめると
・`list_page.dart`ファイルの37行目にある**TextField**に問題がある
・画面のレンダリング中にエラーが起きている
ということが分かりました。
が、見たことがないエラーなのでとりあえずChatGPTに解決策を聞いてみました。

### (コード修正後)
````
- ChatGPT -
提供されたコードを見る限り、TextField ウィジェットがリストビューアイテム内にあります。
これが、レンダリングエラーの原因である可能性があります。
TextField は通常、柔軟な高さを持つウィジェットであり、リストビュー内で使われる場合は注意が必要です。

以下は、TextField をリストビューアイテム内で使う際の改善案です。
具体的には、TextField を包含するコンテナに Expanded ウィジェットを使用して、残りのスペースを適切に分配します。
また、TextField のコントローラーを指定して、各 TextField が独立した状態を持つようにします。
````

````dart
body: Center(
        child: Container(
          // カードリストのUI
          child: ListView.builder(
            itemCount: value,
            itemBuilder: (context, index) {
              // ListItemDateからデータを取得
              String alphabet = ListItemData().alphabets[index];
              TextEditingController textEditingController =
                  TextEditingController();
              return Center(
                child: Card(
                  child: SizedBox(
                    width: double.infinity,
                    height: 100,
                    child: Center(
                      child: Row(
                        children: [
                          Expanded(
                            child: Container(
                              // TODO テスト用のカラーを設定してるため後で編集
                              color: Colors.blue,
                              child: Text(alphabet),
                            ),
                          ),
                          Expanded(
                            child: Container(
                              // TODO テスト用のカラーを設定してるため後で編集
                              color: Colors.red,
                              child: TextField(
                                  decoration: InputDecoration(
                                    border: OutlineInputBorder(),
                                  ),
                                  onChanged: (value) {}),
                            ),
                          ),
                          Row(
                            children: [
                              Container(
                                // TODO テスト用のカラーを設定してるため後で編集
                                color: Colors.red,
                                child: ElevatedButton(
                                  onPressed: () {},
                                  child: Text('追加'),
                                ),
                              ),
                              Container(
                                // TODO テスト用のカラーを設定してるため後で編集
                                color: Colors.red,
                                child: ElevatedButton(
                                  onPressed: () {},
                                  child: Text('削除'),
                                ),
                              ),
                            ],
                          ),
                        ],
                      ),
                    ),
                  ),
                ),
              );
            },
          ),
        ),
      ),
````
ListView内でのTextFieldの設定方法が良くなかったみたい
これでレンダリングエラーが消えました。一安心。

今回の修正と直接は関係無いですが、TextEditingControllerというのも出てきたので
参考として下記の記事も見てみました。
### 参考記事
https://zenn.dev/t_fukuyama/articles/76cb07d38d078a
https://api.flutter.dev/flutter/widgets/TextEditingController-class.html