---
layout: entry
title: ReactNativeコーディング規約.
description: ReactNativeでコーディング規約とアプリケーションを開発する際のルールをまとめた。
---

## このページについて
**ReactNativeでコーディング規約とアプリケーションを開発する際のルールをまとめたページです。**
## コーディング規約
* ベースにするコーディング規約
  * コーディング規約は[Airbnb React/JSX Style Guide](https://github.com/airbnb/javascript/tree/master/react)([日本語版](https://github.com/mitsuruog/javascript-style-guide/tree/master/react))を採用する
     * この[順序](https://github.com/airbnb/javascript/tree/master/react#ordering)通り読みやすい
     * [ReactのLifecycle](https://facebook.github.io/react/docs/react-component.html)に合わせる
         1. ReduxのContainer使えば、mapDispatchToPropsとmapStateToPropsを下に追加する
         2. 任意の static 関数
         3. constructor
         4. getChildContext
         5. componentWillMount
         6. componentDidMount
         7. componentWillReceiveProps
         8. shouldComponentUpdate
         9. componentWillUpdate
         10. componentDidUpdate
         11. componentWillUnmount
         12. onClickSubmit() や onChangeDescription() のようなクリックハンドラやイベントハンドラ
         13. getSelectReason() や getFooterContent() のようなrenderのためのGetter関数
         14. renderNavigation() や renderProfilePicture() のような付随的なrender関数
         15. render
         16. mapDispathToPropsまたはbindAction
         17. mapStateToProps

```
import React, { PropTypes } from 'react';
import { connect } from 'redux'
const propTypes = {
  id: PropTypes.number.isRequired,
  url: PropTypes.string.isRequired,
  text: PropTypes.string,
};

const defaultProps = {
  text: 'Hello World',
};

class Link extends React.Component {
  static methodsAreOk() {
    return true;
  }

  render() {
    return <a href={this.props.url} data-id={this.props.id}>{this.props.text}</a>
  }
}

Link.propTypes = propTypes;
Link.defaultProps = defaultProps;

const mapDispathToProps = (dispatch) => {}
const mapStateToProps = (state) => {}
export default connect(mapDispathToProps,  mapStateToProps)(Link);
```
* リピータの方はReduxも使っている。今まで、それぞれフォルダにファイル一覧が長すぎい
   * こんなフォルダ

```javascript
actions/
  todos.js
components/
  todos/
    TodoItem.js
    ...
constants/
  actionTypes.js
reducers/
  todos.js
index.js
rootReducer.js
```

* この[ブログ](https://jaysoo.ca/2016/02/28/organizing-redux-application/)で解決方法を書きました。
 * 良い方法構造

```javascript
todos/
  components/
  actions.js
  actionTypes.js
  constants.js
  index.js
  reducer.js
index.js
rootReducer.js
```


* タブはスペースで二個か、四個か、使ったほうが良い？
## ツール
* 必要ツール
  * [ESlint](http://eslint.org/)(JS Check Tool)
  * [ESLint-plugin-React](https://github.com/yannickcr/eslint-plugin-react)(React Code Check Tool)
  * [ESLint plugin for React Native](https://github.com/intellicode/eslint-plugin-react-native)
     * ReactNativeのStyleSheetをチェックする
* コマンド
  * http://eslint.org/docs/user-guide/command-line-interface
  * モックアプリの方は開発でインストールしました。
     * ./node_modules/.bin/eslint <folder or file>
  * グローバルでインストールして利用できる。
     * npm install eslint eslint-plugin-react -g
     * eslint <folder or file>
* 設定
  * http://eslint.org/docs/user-guide/configuring
  * モックアプリの設定(.eslintrc)
```javascript
{
    "parser": "babel-eslint",
    "extends": "airbnb", // Airbnb React/JSX Style Guide, 上記した。
    "plugins": [
        "react",  // react code check
        "jsx-a11y", 
        "import",
        "react-native", // react native code check
    ],
    "rules": { // ルール設定
        // "no-underscore-dangle": "off",
        "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }]
    },
    "settings": {
        "import/resolver": {
            "node": {
                "extensions": [".js", ".android.js", ".ios.js"]
            }
        }
    }
}
```

## 開発ツール
* 参照：https://github.com/facebook/react/wiki/Complementary-Tools#editor-integration
 * IDE：[WebStorm](https://www.jetbrains.com/webstorm/)とEditor：VisualStudioCodeは最も良いツールだと思う（※自分の意見）
* Visual Studio Codeアドオン
 * [React Native Tool](https://marketplace.visualstudio.com/items?itemName=vsmobile.vscode-react-native)
 ![React Native Tool](https://raw.githubusercontent.com/Microsoft/vscode-react-native/master/images/react-features.gif)
 * [Reactjs code snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.ReactSnippets)
 ![Reactjs code snippets](https://raw.githubusercontent.com/xabikos/vscode-react/master/images/component.gif)
 ![Reactjs code snippets](https://raw.githubusercontent.com/xabikos/vscode-react/master/images/stateless.gif)

* WebStorm機能
 * VisualStudioCodeの機能を含む
 * ESLintでチェックできる
 * ReactNativeをサポートできる

