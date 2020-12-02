# HelloServlet
ServletでHello worldを出力するまでのプログラムと手順
# 【Java】サーブレットで「Hello world」を表示

「Hello world」をサーブレットで表示する手順についてのまとめメモです。

<!-- ここから 各キャプチャー↓↓↓↓↓↓↓↓↓↓↓↓↓↓ -->
<!-- サンプルコード、サブセクションを記述↓↓↓↓↓ -->

## ① プロジェクトの作成

1. メニューの「ファイル」→「新規」→「その他」を選択
2. 「web」→「動的webプロジェクト」を選択して 「次へ>」
3. プロジェクト名 を入れ( 今回: HelloTest )にして 「次へ>」
4. デフォルトのまま 「次へ>」
5. 「web.xml デプロイメント記述子の生成」にチェックを入れ「完了」

## ② src内にパッケージの作成
今までもパッケージを作成していましたが、

1. プロジェクト内の→「src」を右クリック
2. 「新規」→「パッケージ」を選択
3. パッケージ名を入力( 今回: helloPackage )→「完了」

## ③ クラス（Javaファイル）の作成

通常通り「HelloWorld」クラスを作成する。
[クラス]の作り方については省略。

## ④ HelloWorld.javaにプログラムを書く

「Hello World」と表示するロジックを記述します。

```java
package helloPackage;
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
public class HelloWorld extends HttpServlet{

    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws IOException, ServletException {

        response.setContentType("text/html; charset=Windows-31J");
        PrintWriter out = response.getWriter();
        out.println("<body>Hello World!!</body>");

    }

}
```
## ⑤ web.xmlの編集
入力されたURLと実行されるファイルと紐づけるための処理を書いていきます。

1. 「プロジェクト名(今回: HelloTest)」→「WebContent」→「WEB-INF」→「[web.xml]」
2. [web.xml]内の`web-appタグ内`に以下の【START】〜【END】までのコードを上書きします。

```java
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:web="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
    <!-- 【START】 -->
    <servlet>
        <servlet-name>helloWorld</servlet-name>
        <servlet-class>helloPackage.HelloWorld</servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>helloWorld</servlet-name>
        <url-pattern>/sample</url-pattern>
    </servlet-mapping>
    <!-- 【END】 -->
</web-app>
```

### 【補足】 web.xmlの記述
今回コピペを用意しましたが、サーブレットの命名の仕方についておさらいです。

```java
<web-app>
  <servlet>
    <servlet-name>サーブレットの命名</servlet-name>
    <servlet-class>パッケージ名.サーブレット名</servlet-class>
  </servlet>

  <servlet-mapping>
    <servlet-name>サーブレットの命名</servlet-name>
    <url-pattern>/URLのパターン名</url-pattern>
  </servlet-mapping>

</web-app>
```

## ⑥ 実行
実行して動作確認を行います。

1. プロジェクトを右クリック→「実行」→「サーバーで実行」を選択
2. 既存のサーバーから、作成したサーバーを選択
3. 実行したいリソースが構成済みに入っていることを確認 →「完了」
4. 内部Webブラウザビューが自動で開くので、URLの末にURLのパターン名（今回: sample）を入力
   - [http://localhost:8080/HelloWorld/sample](http://localhost:8080/HelloWorld/sample) 
6. Eclipse内、もしくはブラウザで開いて確認する

<!-- サンプルコードや、サブセクションを記述↑↑↑↑↑ -->
<!-- ここまで 各キャプチャー↑↑↑↑↑↑↑↑↑↑↑↑↑↑↑ -->

<!-- 今後どうするかなどを有れば記述 -->
## 【まとめ】

手順通り行ってコードをコピペでたどり着くかと思いますが、それらロジックについてはまた深堀りして覚えていく必要があります。

ありがとうございました。


<!-- 以下リンク -->

[Progate]:https://prog-8.com/
[ドットインストール]:https://dotinstall.com/
[abstract修飾子]:https://qiita.com/takahirocook/items/9fa0e1cbb8a4dd4e1ff4
[abstract]:https://qiita.com/takahirocook/items/9fa0e1cbb8a4dd4e1ff4
[import]:https://qiita.com/takahirocook/items/59a8a09cab6a98d3bca2
[this]:https://qiita.com/takahirocook/items/d251ec4693c68f6b9538
[super]:https://qiita.com/takahirocook/items/75a07131e7e791c8442c
[final]:https://qiita.com/takahirocook/items/5e0916d9bf28bcf68d0c
[final修飾子]:https://qiita.com/takahirocook/items/5e0916d9bf28bcf68d0c
[List]:https://qiita.com/takahirocook/items/4d622fc6f271569783b5
[length]:https://qiita.com/takahirocook/items/16a123fb73b30869053b
[list]:https://qiita.com/takahirocook/items/4d622fc6f271569783b5
[Map]:https://qiita.com/takahirocook/items/49f46151ecb5e332db32
[map]:https://qiita.com/takahirocook/items/49f46151ecb5e332db32
[set]:https://qiita.com/takahirocook/items/d498329cd26e1500f476
[Set]:https://qiita.com/takahirocook/items/d498329cd26e1500f476
[Date]:https://qiita.com/takahirocook/items/a760e20ef2d9aa5c08fc
[SimpleDateFormat]:https://qiita.com/takahirocook/items/aa857c8f2153193095e4
[Time]:https://qiita.com/takahirocook/items/9caef0bb2409caedba55
[Calendar]:https://qiita.com/takahirocook/items/204dd7331db777eb6f3b
[mainメソッド]:https://qiita.com/takahirocook/items/f4635915337303de338c
[printf()メソッド]:https://qiita.com/takahirocook/items/06d525be63eccd99ed49
[printf()関数]:https://qiita.com/takahirocook/items/06d525be63eccd99ed49
[this]:https://qiita.com/takahirocook/items/d251ec4693c68f6b9538
[getter・setter]:https://qiita.com/takahirocook/items/27828bc8477735612021
[setter]:https://qiita.com/takahirocook/items/27828bc8477735612021
[getter]:https://qiita.com/takahirocook/items/27828bc8477735612021
[new演算子]:https://qiita.com/takahirocook/items/00f9f97592bf50831d39
[new]:https://qiita.com/takahirocook/items/00f9f97592bf50831d39
[static修飾子]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[static]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[web.xml]:https://qiita.com/takahirocook/items/d41a92bd36807d456f82
[GET]:(https://qiita.com/takahirocook/items/8080a478439f6043b2c1)
[GETメソッド]:(https://qiita.com/takahirocook/items/8080a478439f6043b2c1)
[getParameter()]:(https://qiita.com/takahirocook/items/8080a478439f6043b2c1)
[getParameter]:(https://qiita.com/takahirocook/items/8080a478439f6043b2c1)
[getParameterメソッド]:(https://qiita.com/takahirocook/items/8080a478439f6043b2c1)

<!-- あ行 -->
[オブジェクト指向]:https://qiita.com/takahirocook/items/041ba7a096b71ab8ffd4
[継承]:https://qiita.com/takahirocook/items/6c84ea66a6e2ad536a37
[オーバーライド]:https://qiita.com/takahirocook/items/09dd8e5f56d6617ce45a
[オーバーロード]:https://qiita.com/takahirocook/items/b937c3c07126fe7e02a4
[インスタンス]:https://qiita.com/takahirocook/items/ec01cdcbb440cf0d1cc4
[インスタンス化]:https://qiita.com/takahirocook/items/ec01cdcbb440cf0d1cc4
[アクセス修飾子]:https://qiita.com/takahirocook/items/e51b0b9d37d95ad587fe
[インスタンス化]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[インスタンス変数]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[インターフェイス]:https://qiita.com/takahirocook/items/ca84be8dfef664b19194
[インターフェース]:https://qiita.com/takahirocook/items/ca84be8dfef664b19194
[インポート]:https://qiita.com/takahirocook/items/59a8a09cab6a98d3bca2
[インデックス]:https://qiita.com/takahirocook/items/16a123fb73b30869053b
<!-- か行 -->
[拡張for文]:https://qiita.com/takahirocook/items/470b2858de1a4f99b334
[クラスメソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[クラスフィールド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[クラス変数]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[カプセル化]:https://qiita.com/takahirocook/items/e469a7c0539a0012868e
[クラス]:https://qiita.com/takahirocook/items/50cbbdca8e21539170e9
[コンストラクタ]:https://qiita.com/takahirocook/items/fa1822f2f22c3786593e
<!-- さ行 -->
[書式指定子]:https://qiita.com/takahirocook/items/06d525be63eccd99ed49
[静的メソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[静的変数]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[静的メソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[スーパークラス]:https://qiita.com/takahirocook/items/75a07131e7e791c8442c
<!-- た行 -->
[定数]:https://qiita.com/takahirocook/items/5e0916d9bf28bcf68d0c
[抽象クラス]:https://qiita.com/takahirocook/items/9fa0e1cbb8a4dd4e1ff4
[抽象メソッド]:https://qiita.com/takahirocook/items/9fa0e1cbb8a4dd4e1ff4
[動的メソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
<!-- な行 -->
[日時の文字列操作]:https://qiita.com/takahirocook/items/aa857c8f2153193095e4
<!-- は行 -->
[パッケージ]:https://qiita.com/takahirocook/items/39b58d17abcb159ef5c1
[引数]:https://qiita.com/takahirocook/items/5e5b0ba79e869f4a592e
[配列]:https://qiita.com/takahirocook/items/16a123fb73b30869053b
[配列操作]:https://qiita.com/takahirocook/items/16a123fb73b30869053b
[日付操作]:https://qiita.com/takahirocook/items/9caef0bb2409caedba55
[フィールド]:https://qiita.com/takahirocook/items/28df75a133049a74ece1
[フィールド変数]:https://qiita.com/takahirocook/items/28df75a133049a74ece1
[インスタンスフィールド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
<!-- ま行 -->
[戻り値]:https://qiita.com/takahirocook/items/3b6fa670a1d6dd4a9386
[メソッド]:https://qiita.com/takahirocook/items/5bfe43576d87a2a4006c
[メソッドの呼び出し]:https://qiita.com/takahirocook/items/f4635915337303de338c
<!-- や行 -->
<!-- ら行 -->
<!-- わ行 -->
