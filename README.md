## Part 2: HTML

- `fn consume_char()`
  - 1文字進める
  - Rust の文字列はUTF-8のバイト列なので、次の文字列に進めるために単純に1バイト進めるだけだとマルチバイト文字列に対応できない
  - -> `char_indices()` というメソッドを使うといい

```rust
// Return the current character, and advance self.pos to the next character.
fn consume_char(&mut self) -> char {
    let mut iter = self.input[self.pos..].char_indices();
    let (_, cur_char) = iter.next().unwrap();
    let (next_pos, _) = iter.next().unwrap_or((1, ' '));
    self.pos += next_pos;
    return cur_char;
}
```

## Part 3: CSS

- simple selector のみ
  - combinators で結合されたセレクタのチェインは対象外
- Specificity 詳細度
  - スタイルのコンフリクト時、どのスタイルをoverrideするかを決める方法
  - classよりid



## Part 4: Style
- DOM と CSS ルールを入力として、各ノードに適用する CSS プロパティの値を決定する処理
  - Style Tree と呼ぶ <- CSSOM と同じかな？
- 仕様でいう [Assigning property values, Cascading, and Inheritance](https://www.w3.org/TR/CSS2/cascade.html)
- Selector Matching
  - simple selector しかサポートしてないので簡単
  - simple selector がある要素にマッチするかどうかは、その要素だけを見ればいいので

- 🤔 `fn matches_simple_selector()`

`if selector.tag_name.iter().any(|name| elem.tag_name != *name)` というようにイテレータが登場する理由がわからない。 `tag_name` って１個のタグ名じゃないの？
