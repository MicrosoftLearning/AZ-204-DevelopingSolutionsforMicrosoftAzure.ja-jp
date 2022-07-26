---
ms.openlocfilehash: 40d663462e7e48bf5baeb118e1da99d4ebf89c86
ms.sourcegitcommit: b3c9969e988713afd5bfcfa551d5986d914edf2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2022
ms.locfileid: "146565022"
---
# <a name="az-204-developing-solutions-for-microsoft-azure"></a>AZ-204: Microsoft Azure 向けのソリューションの開発

**すべてのラボの手順は、2021 年 10 月 15 日に更新されました。** 現在未解決のすべての問題と PR を終了し、全員に新しい手順を確認するように促し、今後は新しい変更を送信します。

> **注**:ラボ ホスティング プロバイダーから AllFiles が提供されない場合、学生はリポジトリを同期するように指示されるはずです。 

- ラボでの手順を示した使いやすい一覧について、[https://aka.ms/az204labs](https://aka.ms/az204labs) にアクセスするように **受講者に指示します**。
- **あなたは MCT ですか?** - [MCT 向けの GitHub ユーザー ガイド](https://microsoftlearning.github.io/MCT-User-Guide/)をご覧ください
- **ラボの手順を手動で作成する必要がありますか?** - 手順は、[MicrosoftLearning/Docker-Build](https://github.com/MicrosoftLearning/Docker-Build) リポジトリで確認できます 
- イシュー/PR の進行状況を追跡する[プロジェクト](https://github.com/MicrosoftLearning/AZ-204-DevelopingSolutionsforMicrosoftAzure/projects/1)を追加しました。

## <a name="security-issue---february-2022"></a>セキュリティの問題 - 2022 年 2 月

一部の Azure トレーニング ラボでは、特定のユーザー名とパスワードを使用するように受講者に指示しています。 悪意のあるアクターは、絶えず仮想マシンをスキャンし、これらの資格情報を使用してログインを試みます。
いったんログインされると、そのマシンがクリプト マイニングに使用され、他の操作に使用される可能性があります。

**修復**: 自分で選択したパスワードを使用するように受講生に指示する必要があります。 ラボの手順で、受講生にこのパスワードを使用させないようにしてください。 このラボの手順は、今週、パスワードを削除するように更新されます。 

## <a name="what-are-we-doing"></a>ここでの内容

- このコースをサポートするには、コースで使用される Azure サービスを最新の状態に保つために、コース コンテンツを頻繁に更新する必要があります。  ラボの手順とラボ ファイルは GitHub で公開しています。これにより、コースの作成者と MCT 間でのオープンな作業が可能となり、Azure プラットフォームの変更に合わせてコンテンツを最新の状態に保つことができます。

- これにより、今まで経験したことがないようなコラボレーション感がラボに生まれると期待しています。Azure が変更され、ライブ配信中にあなたがそれを最初に見つけた場合は、ラボ ソースで機能強化を行ってください。 

## <a name="how-should-i-use-these-files-relative-to-the-released-moc-files"></a>リリースされた MOC のファイルに対してこれらのファイルを使用する方法

- 講師ハンドブックと PowerPoint は、引き続きコースのコンテンツを教えるための主要なソースになるでしょう。

- GitHub 上のこれらのファイルは学生ハンドブックと組み合わせて使用するように設計されています。ただし、中央リポジトリとして GitHub 内にあるので、MCT とコース作成者が最新のラボ ファイルの共有ソースを持っている可能性があります。

- すべての配信について、トレーナーは最新の Azure サービスをサポートするために行われた可能性がある変更を GitHub で確認し、配信用の最新のファイルを取得することをお勧めします。

## <a name="what-about-changes-to-the-student-handbook"></a>受講者ハンドブックの変更については?

- 受講者ハンドブックは四半期ごとに見直し、必要があれば通常の MOC リリースの手順を通して更新します。

## <a name="how-do-i-contribute"></a>貢献するには?

- すべての MCT は、GitHub repro のコードまたはコンテンツに pull request を送信できます。Microsoft とコース作成者は、必要に応じてコンテンツとラボ コードの変更をトリアージして追加します。

- バグ、変更、改善、アイデアを送信できます。  新しい Azure 機能を先に見つけたら、  新しいデモを提出しましょう。

## <a name="notes"></a>Notes

### <a name="classroom-materials"></a>コース資料

MCT とパートナーが、これらの資料にアクセスし、学生に個別に提供することを強く推奨します。  進行中のクラスの一部としてラボ ステップにアクセスできるように、学生に直接 GitHub を指示するには、学生がコースの一部として別の UI にもアクセスする必要がありますが、これは混乱の原因となります。 個別のラボの手順を受け取る理由を学生に説明すると、クラウドベースのインターフェイスとプラットフォームが常に変化しているという性質を強調できます。 GitHub 上のファイルにアクセスするための Microsoft Learning サポートと GitHub サイトのナビゲーションのサポートは、このコースを教える MCT のみに限定されています。