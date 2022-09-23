---
ms.openlocfilehash: 011ce36305066f1093b71a6f2bcb81da5b1df381
ms.sourcegitcommit: bd0615f0fd0c1bbe335dacbb6e22ec4e6134a207
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2022
ms.locfileid: "146467048"
---
# <a name="contributing-to-microsoft-learning-repositories"></a>Microsoft Learning リポジトリへの貢献

MCT の貢献は、Azure プラットフォームの変更に合わせてラボおよびデモ コンテンツを最新の状態に保つための重要な要素です。 ラボファイルの変更をできる限り簡単にしたいと考えています。 変更を投稿する場合は、次のガイドラインに留意してください。

## <a name="github-use--purpose"></a>GitHub の使用と目的

Microsoft Learn では、GitHub を使用して、Azure などのクラウド サービスをカバーするコースのラボ ステップとラボ スクリプトを公開しています。 GitHubを使用すると、コースの作成者と MCT が Azure プラットフォームの変更に合わせてラボ コンテンツを最新の状態に保つことができます。 GitHub を使用すると、MCT はラボの変更に関するフィードバックや提案を提供でき、コースの作成者はラボの手順とスクリプトをすばやく比較的簡単に更新できます。

> これらのコースを教える準備をするときは、GitHub から適切なファイルをダウンロードして、最新のラボ手順とスクリプトを使用していることを確認する必要があります。 GitHub を使用して、コースの技術的な内容や準備方法を議論することはできません。 ラボの変更に対処するためにのみ使用してください。

MCT とパートナーが、これらの資料にアクセスし、学生に個別に提供することを強く推奨します。  進行中のクラスの一部としてラボ ステップにアクセスできるように、学生に直接 GitHub を指示するには、学生がコースの一部として別の UI にもアクセスする必要がありますが、これは混乱の原因となります。 個別のラボの手順を受け取る理由を学生に説明すると、クラウドベースのインターフェイスとプラットフォームが常に変化しているという性質を強調できます。 GitHub 上のファイルにアクセスするための Microsoft Learning サポートと GitHub サイトのナビゲーションのサポートは、このコースを教える MCT のみに限定されています。

> 受講者を GitHub リポジトリに直接ポイントする代わりに、受講者に GitHub Pages Web サイトをポイントして演習の手順を表示することもできます。 GitHub ページ Web サイトの URL は、リポジトリの上部にあります。

コースとデモに関する一般的なコメント、またはコース配信の準備方法については、既存の MCT フォーラムを使用してください。

## <a name="how-can-i-collaborate"></a>共同作業を行う方法

GitHub アカウントをまだお持ちでない場合は、[作成](https://github.com/join)してください。 GitHub プロファイルで提携を識別します。 

### <a name="reporting-issues"></a>問題の報告

最新バージョンのラボの指示に問題がある場合は、パブリック リポジトリから **イシュー** を開くことができます。 イシュー テンプレートで指定されている情報 (イシューまたはフィードバック) を入力してください。

- **問題を説明** し、保守管理者が問題を再現するのに役立つ追加の詳細を含めます。
- テンプレートで説明されているように、イシューには **明確でわかりやすいタイトルを使用** して問題を特定します。
- できるだけ多くの詳細で **問題を再現する正確な手順を説明** します。
- 説明した手順に従っていることを示し、問題を明確に示す **スクリーンショットを含めます**。



### <a name="pull-requests"></a>pull request

イシューの修正や更新の提案を共同で行う場合は、Pull Request (PR) を作成してください。

#### <a name="easy-prs-using-github-no-gitgithub-knowledge-needed"></a>GitHub を使用した簡単な PR (git/github の知識は必要ありません)
Git/GitHub の経験 (リポジトリのフォークや、Git リポジトリのローカルでの操作) が十分にない可能性があるユーザーのために、ここでは、GitHub Web サイトを使用して Pull Request を提案する簡単な方法を説明します。



https://user-images.githubusercontent.com/64772417/137773529-9cad5c7f-2841-4efc-965e-c2c727eb769f.mp4



> ⚠️ このオプションは、Git/GitHub の経験がないユーザーに推奨されます。同じプロセスを手動で実行できます。[GitHub、フォークの操作](https://docs.github.com/en/github/collaborating-with-pull-requests/working-with-forks)

#### <a name="creating-a-pull-request"></a>Pull Request の作成

既存のイシューまたは提案に対して Pull Request を作成している可能性があります。 Pull Request が既存のイシューに関連している場合は、Pull Request の説明の「**修正 #[Issue-Number]** 」セクションに **イシュー** 番号を指定してリンクします ("[]" も置き換えます)。 

> ⚠️ Pull Request が、まだ報告されていないイシューに関連している場合は、[前述](https://github.com/MicrosoftLearning/AZ400-DesigningandImplementingMicrosoftDevOpsSolutions/blob/master/.github/CONTRIBUTING.md#reporting-issues)の手順に従って報告してください。 

Pull Request タイトルには、次の構文を使用します。

`[Issue/Proposal]-[M00]-[LABNAME]:[QUICK_DESCRIPTION]`

#### <a name="creatingupdating-screenshots-lab-1"></a>スクリーンショットの作成/更新 (ラボ 1)

一部の手順で使用されているスクリーンショットは、`AZ400-DesigningandImplementingMicrosoftDevOpsSolutions/Instructions/Labs/images` の下にあるフォルダーでラボ番号を使用して次のように整理されています。 

![Images フォルダーを示す Github リポジトリ](images/image_folder_location.png)

ラボ固有のフォルダーでは、スクリーンショットは次の形式 (PNG) と名前で保存されます: `[descriptive_name]_[versionnumber].png` (例: `create_epic_v1.png`)

スクリーンショットを更新する必要がある場合、新しいものはバージョン番号 `create_epic_v1.png` を `create_epic_v2.png` にインクリメントし、対応する **images** フォルダーにアップロードされ、Pull Request の一部として既存のものを削除します。

ラボの手順のスクリーンショットを参照して使用する場合は、次に示すようにイメージを追加する必要があります。

`![Description for the image, ALT Text](image reference)`

たとえば、次のように入力します。

`![Azure DevOps Generator website. Click on "Sign In" option](images/m1/demo_signin_v1.png)`

> ⚠️ アクセス性を高めるには、上の例に示すように、ALT テキストにスクリーンショットの **明確** な説明が含まれている必要があります。

> ⚠️ 次の構文例を使用してイメージのサイズを変更し、ニーズに合わせて変更できます: `[<img src="images/m1/child_feature_v1.png" alt="Include Title 'Training Dashboard' and click 'OK' " width="500"/>]()`

#### <a name="taking-and-editing-screenshots-lab-1"></a>スクリーンショットの取得と編集 (ラボ 1)

Microsoft 認定トレーナー (MCT) の場合、TechSmith はインフルエンサー プログラムの一環として **Snagit** を提供しています。 https://discover.techsmith.com/techsmith-influencer-program/ で今すぐ適用してください。

[Snagit](https://www.techsmith.com/screen-capture.html) は、画面をキャプチャするための優れたツールであり、スクリーンショットに追加する機能に役立つツールを提供します。

**Snagit** を使用したスクリーンショットは、次のようになります。
- Azure portal、Azure DevOps、GitHub などの Web サイト/アプリ用のライト テーマ (濃色またはカスタムではない) を使用するツールがあります。
- 個人情報 (名前、電子メール、プロフィール画像...) は表示 **せず**、**ぼかし** 機能を使用します。
- 強調表示には **赤い四角形** を使用します。
- **ステップ** を使用して、表示されるアクションの番号付きシーケンスを適用します (**赤い四角形** を一緒に使用します)。

それらすべてに次のプロパティ (ぼかし、赤い四角形、ステップ) があります:

[<img src="images/blur.png" alt="blur properties " width="266"/>]() [<img src="images/red_rectangle.png" alt="red rectangle properties" width="271"/>]() [<img src="images/steps.png" alt="steps properties" width="260"/>]()

例:

 !["イテレーション" タブで、"イテレーションの選択" をクリックします](images/select_iteration_v1.png)

## <a name="additional-resources"></a>その他のリソース

GitHub を初めて使用する MCT 向けのユーザー ガイドが提供されています。 GitHub への接続、コース教材のダウンロードと印刷、受講者が演習で使用するスクリプトの更新、およびこのコースのコンテンツを最新の状態に保つ方法について説明する手順について説明します。

<https://microsoftlearning.github.io/MCT-User-Guide/>
