---
title: Ajouter de nouvelles connexions
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5f6f34c28a6bbba236a4d90e2f936fad0b2a3f60
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283058"
---
# <a name="add-new-connections"></a>Ajouter de nouvelles connexions

Vous pouvez tester votre connexion à une base de données ou à un service, et explorer le contenu et les schémas de la base de données, à l’aide de **Explorateur de serveurs**, **Cloud Explorer**ou **Explorateur d’objets SQL Server**. La fonctionnalité de ces fenêtres chevauche dans une certaine mesure. Les différences de base sont les suivantes :

- Explorateur de serveurs

   Installé par défaut dans Visual Studio. Peut être utilisé pour tester les connexions et afficher SQL Server bases de données, toutes les autres bases de données qui ont un fournisseur ADO.NET installé et certains services Azure. Affiche également des objets de bas niveau tels que les compteurs de performances système, les journaux des événements et les files d’attente de messages. Si une source de données n’a pas de fournisseur ADO.NET, elle n’apparaît pas ici, mais vous pouvez toujours l’utiliser à partir de Visual Studio en vous connectant par programme.

- Cloud Explorer

   Installez cette fenêtre manuellement en tant qu’extension Visual Studio à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS). Fournit des fonctionnalités spécialisées pour l’exploration et la connexion aux services Azure.

- Explorateur d’objets SQL Server

   Installé avec SQL Server Data Tools et visible dans le menu **affichage** . Si vous ne le voyez pas, accédez à **programmes et fonctionnalités** dans le panneau de configuration, recherchez Visual Studio, puis sélectionnez **modifier** pour réexécuter le programme d’installation après avoir activé la case à cocher pour SQL Server Data Tools. Utilisez **Explorateur d’objets SQL Server** pour afficher les bases de données SQL (si elles ont un fournisseur ADO.net), créer des bases de données, modifier des schémas, créer des procédures stockées, récupérer des chaînes de connexion, afficher les données, et bien plus encore. Les bases de données SQL qui n’ont pas de fournisseur ADO.NET installé ne s’affichent pas ici, mais vous pouvez toujours vous y connecter par programmation.

## <a name="add-a-connection-in-server-explorer"></a>Ajouter une connexion dans Explorateur de serveurs

Pour créer une connexion à la base de données, cliquez sur l’icône **Ajouter une connexion** dans **Explorateur de serveurs**, ou cliquez avec le bouton droit dans **Explorateur de serveurs** sur le nœud **connexions de données** , puis sélectionnez Ajouter une **connexion**. À partir de là, vous pouvez également vous connecter à une base de données sur un autre serveur, un service SharePoint ou un service Azure.

![Icône Explorateur de serveurs nouvelle connexion](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

La boîte de dialogue **Ajouter une connexion** s’affiche. Ici, nous avons entré le nom de l’instance SQL Server de la base de données locale.

![Ajouter une nouvelle connexion](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Modifier le fournisseur

Si la source de données n’est pas ce que vous souhaitez, cliquez sur le bouton **modifier** pour choisir une nouvelle source de données et/ou un nouveau fournisseur de données ADO.net. Le nouveau fournisseur peut demander vos informations d’identification, en fonction de la façon dont vous les avez configurées.

![Modifier le Fournisseur de données AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Tester la connexion

Une fois que vous avez choisi la source de données, cliquez sur **tester la connexion**. En cas d’échec, vous devrez résoudre les problèmes en fonction de la documentation du fournisseur.

![Tester la connexion](../data-tools/media/raddata-test-connection.png)

Si le test s’effectue correctement, vous êtes prêt à créer une *source de données*, qui est un terme Visual Studio qui signifie vraiment un modèle de *données* basé sur la base de données ou le service sous-jacent.

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
