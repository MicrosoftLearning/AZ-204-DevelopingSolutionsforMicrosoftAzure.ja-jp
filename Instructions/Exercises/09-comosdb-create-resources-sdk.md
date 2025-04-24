---
lab:
  title: .NET を使用して NoSQL 向け Azure Cosmos DB リソースを作成する
  description: Microsoft .NET SDK v3 を使用して Azure Cosmos DB 内でデータベース リソースとコンテナー リソースを作成する方法について説明します。
---

# .NET を使用して NoSQL 向け Azure Cosmos DB リソースを作成する

この演習では、Azure Cosmos DB 内にコンテナー、データベース、および項目を作成するコンソール アプリを作成します。

この演習で実行されるタスク:

* Azure Cosmos DB アカウントを作成する
* コンソール アプリの作成
* コンソール アプリを実行して結果を確認する

この演習の所要時間は約 **30** 分です。

## 開始する前に

開始する前に、以下の要件が満たされていることを確認してください。

* Azure サブスクリプション。 まだお持ちでない場合は、[Microsoft Azure にサインアップ](https://azure.microsoft.com/)できます。

## Azure Cosmos DB アカウントを作成する

演習のこのセクションでは、リソース グループと Azure Cosmos DB アカウントを作成します。 また、エンドポイントとアカウント用アクセス キーも記録します。

1. お使いのブラウザーで Azure portal ([https://portal.azure.com](https://portal.azure.com)) に移動し、メッセージに応じて Azure 資格情報を使用してサインインします。

1. ページ上部の検索バーの右側にある **[\>_]** ボタンを使用して、Azure portal 内に新しいクラウド シェルを作成します。***Bash*** 環境を選択すること。 Azure portal の下部にあるペインに、Cloud Shell のコマンド ライン インターフェイスが表示されます。

    > **注**: *PowerShell* 環境を使用するクラウド シェルを以前に作成している場合は、それを ***Bash*** に切り替えること。

1. Cloud Shell ツール バーの **[設定]** メニューで、**[クラシック バージョンに移動]** を選択します (これはコード エディターを使用するのに必要です)。

1. この演習に必要なリソースのリソース グループを作成します。 **\<myResourceGroup>** を、使用するリソース グループの名前に置き換えます。 必要に応じて、**useast** を最寄りのリージョンに置き換えることができます。 

    ```
    az group create --location useast --name <myResourceGroup>
    ```

1. 次のコマンドを実行して Azure Cosmos DB アカウントを作成します。 **\<myCosmosDBacct>** を、Azure Cosmos DB アカウントを識別するための "一意の" 名前に置き換えます。** **\<myResourceGroup>** は前の手順で選択した名前に置き換えること。

    >**注:** アカウント名に含めることができるのは、英小文字、数字、ハイフン (-) のみです。 長さは 3 文字から 31 文字でなければなりません。 *このコマンドが完了するまでに数分かかります。*

    ```
    az cosmosdb create -n <myCosmosDBacct> -g <myResourceGroup>
    ```

1.  次のコマンドを実行して、Azure Cosmos DB アカウントの **documentEndpoint** を取得します。 コマンド結果に表示されるエンドポイントを記録しておきます。これは演習の後半で必要になります。 **\<myCosmosDBacct>** と **\<myResourceGroup>** を、それぞれ作成した名前に置き換えます。

    ```bash
    az cosmosdb show -n <myCosmosDBacct> -g <myResourceGroup> --query "documentEndpoint" --output tsv
    ```

1. 次のコマンドを使用して、アカウントの主キーを取得します。 コマンド結果に表示される **primaryMasterKey** を、コード内で使用できるよう記録しておきます。 **\<myCosmosDBacct>** と **\<myResourceGroup>** を、それぞれ作成した名前に置き換えます。

     ```
    # Retrieve the primary key
    az cosmosdb keys list -n <myCosmosDBacct> -g <myResourceGroup>
    ```

## コンソール アプリケーションを作成する

必要なリソースが Azure にデプロイされたので、次の手順として、Visual Studio Code で同じターミナル ウィンドウを使用してコンソール アプリケーションをセットアップします。

1. プロジェクト用のフォルダーを作成し、フォルダーに移動します。

    ```bash
    mkdir cosmosdb
    cd cosmosdb
    ```

1. .NET コンソール アプリを作成します。

    ```dotnetcli
    dotnet new console --framework net8.0
    ```

1. 次のコマンドを実行して、**Microsoft.Azure.Cosmos** パッケージ、およびサポートする **Newtonsoft.Json** パッケージをプロジェクトに追加します。

    ```dotnetcli
    dotnet add package Microsoft.Azure.Cosmos --version 3.*
    dotnet add package Newtonsoft.Json --version 13.*
    ```

次に、クラウド シェル内のエディターを使用して、**Program.cs** ファイル内のテンプレート コードを置き換えます。

### プロジェクトの開始コードを追加する

1. アプリケーションの編集を開始するには、クラウド シェル内で次のコマンドを実行します。

    ```bash
    code Program.cs
    ```

1. **using** ステートメントの後の既存のコードを、次のコード スニペットに置き換えます。 コード コメントの指示に従って、**\<documentEndpoint>** と **\<primaryKey>** のプレースホルダーの値を必ず置き換えてください。

    このコードは、アプリの全体的な構造と、いくつかの必要な要素を提供します。 コード内のコメントを確認し、手順で指定された各領域にコードを追加します。 

    ```csharp
    using Microsoft.Azure.Cosmos;
    
    namespace CosmosExercise
    {
        // This class represents a product in the Cosmos DB container
        public class Product
        {
            public string? id { get; set; }
            public string? name { get; set; }
            public string? description { get; set; }
        }
    
        public class Program
        {
            // Cosmos DB account URL - replace with your actual Cosmos DB account URL
            static string cosmosDbAccountUrl = "<documentEndpoint>";
    
            // Cosmos DB account key - replace with your actual Cosmos DB account key
            static string accountKey = "<primaryKey>";
    
            // Name of the database to create or use
            static string databaseName = "myDatabase";
    
            // Name of the container to create or use
            static string containerName = "myContainer";
    
            public static async Task Main(string[] args)
            {
                // Create the Cosmos DB client using the account URL and key
    
    
                try
                {
                    // Create a database if it doesn't already exist
    
    
                    // Create a container with a specified partition key
    
    
                    // Define a typed item (Product) to add to the container
    
    
                    // Add the item to the container
                    // The partition key ensures the item is stored in the correct partition
    
    
                }
                catch (CosmosException ex)
                {
                    // Handle Cosmos DB-specific exceptions
                    // Log the status code and error message for debugging
                    Console.WriteLine($"Cosmos DB Error: {ex.StatusCode} - {ex.Message}");
                }
                catch (Exception ex)
                {
                    // Handle general exceptions
                    // Log the error message for debugging
                    Console.WriteLine($"Error: {ex.Message}");
                }
            }
        }
    }
    ```

### コードの追加によりクライアントを作成して操作を実行する 

演習のこのセクションでは、プロジェクトの指定された各領域にコードを追加して、クライアント、データベース、コンテナーを作成し、サンプル項目をコンテナーに追加します。

1. **// Create the Cosmos DB client using the account URL and key** コメントの後のスペースに次のコードを追加します。 このコードにより、お使いの Azure Cosmos DB アカウントへの接続に使用するクライアントを定義します。

    ```csharp
    CosmosClient client = new(
        accountEndpoint: cosmosDbAccountUrl,
        authKeyOrResourceToken: accountKey
    );
    ```

    >注: *Azure Identity* ライブラリの **DefaultAzureCredential** を使用することをお勧めします。 サブスクリプションの設定内容によっては、Azure 内で追加の構成要件が必要な場合があります。 

1. **// Create a database if it doesn't already exist** コメントの後のスペースに次のコードを追加します。 

    ```csharp
    Microsoft.Azure.Cosmos.Database database = await client.CreateDatabaseIfNotExistsAsync(databaseName);
    Console.WriteLine($"Created or retrieved database: {database.Id}");
    ```

1. **// Create a container with a specified partition key** コメントの後のスペースに次のコードを追加します。 

    ```csharp
    Microsoft.Azure.Cosmos.Database database = await client.CreateDatabaseIfNotExistsAsync(databaseName);
    Console.WriteLine($"Created or retrieved database: {database.Id}");
    ```

1. **// Define a typed item (Product) to add to the container** コメントの後のスペースに次のコードを追加します。 これにより、コンテナーに追加される項目を定義します。

    ```csharp
    Product newItem = new Product
    {
        id = Guid.NewGuid().ToString(), // Generate a unique ID for the product
        name = "Sample Item",
        description = "This is a sample item in my Azure Cosmos DB exercise."
    };
    ```

1. **// Add the item to the container** コメントの後のスペースに次のコードを追加します。 

    ```csharp
    ItemResponse<Product> createResponse = await container.CreateItemAsync(
        item: newItem,
        partitionKey: new PartitionKey(newItem.id)
    );
    ```

1. コードが完了したら、**ctrl + q** を使用してファイルを保存することにより作業内容を保存し、次に **ctrl + q** を使用してエディターを終了します。

1. クラウド シェル内で次のコマンドを実行して、プロジェクト内にエラーがないかテストします。 エラーが表示された場合は、エディターで *Program.cs* ファイルを開き、欠損コードや貼り付けエラーがないか確認します。

    ```bash
    dotnet build
    ```

プロジェクトが完了したら、アプリケーションを実行し、Azure portal で結果を確認します。

## アプリケーションの実行と結果の確認

1. クラウド シェル内の場合には、`dotnet run` コマンドを実行します。 次のような内容が出力されます。

    ```
    Created or retrieved database: myDatabase
    Created or retrieved container: myContainer
    Created item: c549c3fa-054d-40db-a42b-c05deabbc4a6
    Request charge: 6.29 RUs
    ```

1. Azure portal 内で、前の手順に作成した Azure Cosmos DB アカウントに移動します。 左側のナビゲーションで、**[Data Explorer]** を選択します。 **Data Explorer** で **[myDatabase]** を選択し、次に **[myContainer]** を展開します。 作成した項目を表示するには、**[Items]** を選択します。

    ![データ エクスプローラー内の項目の位置を示すスクリーンショット。](./media/09/cosmos-data-explorer.png)

## リソースをクリーンアップする

これで演習が完了したので、不要なリソース使用を避けるために、作成したクラウド リソースを削除してください。

1. 作成したリソース グループに移動し、この演習で使用したリソースの内容を表示します。
1. ツール バーの **[リソース グループの削除]** を選びます。
1. リソース グループ名を入力し、削除することを確認します。
