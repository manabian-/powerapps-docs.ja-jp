ここまでのコースで、web.powerapps.com での作業にいくらかの時間を費やしてきました。つまり、お気づきかどうかわかりませんが、ずっと特定の*環境*で作業をしてきたということです。 環境とは、単にアプリとその他のリソースがグループ化されたものを指します (詳細は後ほど説明します)。 web.powerapps.com の画面の右上を見ると、現在の環境を表示するドロップダウン メニューがあります。

![環境のピッカー](./media/learning-manage-environments/environment-picker.png)

PowerApps を初めてご利用の場合、現時点では既定の環境しかないかもしれません。 メニューをクリックまたはタップして、その他の環境が利用可能かどうかを確認します。

## <a name="why-use-environments"></a>環境を使用する理由
環境とは、データ接続や Microsoft Flow からのフローなど、アプリおよびその他のリソース用のコンテナーを指します。 ビジネス要件に基づいてグループ化する方法です。 既定のものに加えて追加の環境を作成することには、いくつかの理由があります。

* **部署ごとに独立してアプリを開発**: 大規模な組織では、各部署が別々の環境で作業できます。
* **アプリケーション ライフサイクル管理 (ALM) のサポート**: 開発中のアプリと、既に開発が完了して共有しているアプリに、別々の環境を用意できます。
* **データ アクセスの管理**: 各環境が別々の Common Data Service データベースを持つことができ、その他のデータ接続は環境特有のものとなります (つまり、環境間で共有されません)。

1 つ留意する点として、環境はアプリ作成者と PowerApps 管理者にしか関連しません。 ユーザーにアプリを共有すると、そのユーザーは適切なアクセス許可さえあれば、あとはアプリを実行するだけです。 ユーザーは、アプリがどの環境のものであるかについて心配する必要がありません。

## <a name="create-an-environment"></a>環境の作成
ここまでこのコースでは、アプリ作成者に焦点を置いてきましたが、環境は管理者によって作成され、管理されるものです。 管理者でない場合でも、環境の設定について管理者に話すときに、この情報は役に立ちます。 PowerApps 管理センターで、**[環境]**、**[新しい環境]** の順にクリックまたはタップします。 **[新しい環境]** の画面で、環境名を入力して、リージョンを選択します。その環境に Common Data Service データベースを作成するかどうかを選択して、**[Create an environment (環境を作成)]** をクリックまたはタップします。

![環境の作成](./media/learning-manage-environments/create-environment.png)

これで、新しい環境で作業ができるようになりました。 web.powerapps.com に戻ると、[環境] のドロップダウン メニューに新しい環境が表示されます。

## <a name="manage-access-to-an-environment"></a>環境へのアクセス権の管理
次の場合、環境にアクセスすることができます。

* **Environment Admin**: 環境内で完全なアクセス許可があります。
* **Environment Maker**: すべてのアプリを参照、作成し、Common Data Service で作業できます (他のアクセス許可が適用されます)。

管理者として、**[環境]** タブから環境へのアクセス許可を付与できます。最初に、環境をクリックまたはタップします。 ユーザー (この例では**Environment Maker**) を追加するには、**[Environment roles (環境ロール)]****[Environment Maker]** の順にクリックまたはタップします。 そこから、ロールにユーザーまたはグループを追加して、**[保存]** をクリックします。

![環境へのアクセスの管理](./media/learning-manage-environments/environment-access.png)

環境のメリット、作成方法、アクセス許可の方法について説明してきました。 管理者ロールではない場合でも、この仕組みを知っておくと役に立ちます。 アプリの管理に関するセクションはこれで終了です。データの管理に関する次のセクションに進む準備ができました。こちらでは、Common Data Service に焦点を当てます。
