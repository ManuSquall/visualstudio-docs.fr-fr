---
title: Ajouter de nouvelles connexions
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b01af2aa269cbaddbd84d24827b1a77e97d52d8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818468"
---
# <a name="add-new-connections"></a>Ajouter de nouvelles connexions

Vous pouvez tester votre connexion à une base de données ou un service et Explorer le contenu de la base de données et des schémas, à l’aide **Explorateur de serveurs**, **Cloud Explorer**, ou **Explorateur d’objets SQL Server**. Les fonctionnalités de ces fenêtres se chevauchent dans une certaine mesure. Les principales différences sont :

- Explorateur de serveurs

   Installé par défaut dans Visual Studio. Peut être utilisé pour tester les connexions et afficher les bases de données SQL Server, les autres bases de données ayant un fournisseur ADO.NET installé et certains services Azure. Montre également les objets de bas niveau tels que les compteurs de performances système, les journaux des événements et les files d’attente. Si une source de données n’a aucun fournisseur ADO.NET, il n’apparaît pas ici, mais vous pouvez toujours utiliser il à partir de Visual Studio en vous connectant par programmation.

- Cloud Explorer

   Installez cette fenêtre manuellement comme une extension de Visual Studio à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS). Fournit des fonctionnalités spécialisées pour l’exploration et la connexion aux services Azure.

- Explorateur d'objets SQL Server

   Installé avec SQL Server Data Tools et visible sous le **vue** menu. Si vous n’apparaît pas, accédez à **programmes et fonctionnalités** dans le panneau de configuration, recherchez Visual Studio, puis sélectionnez **modification** exécuter à nouveau le programme d’installation après avoir sélectionné la case à cocher pour SQL Server Data Tools. Utilisez **Explorateur d’objets SQL Server** vue SQL bases de données (si elles ont un fournisseur ADO.NET), créer de nouvelles bases de données, modifier des schémas, créer des procédures stockées, récupérer les chaînes de connexion, afficher les données et bien plus encore. Les bases de données SQL disposant d’aucun fournisseur ADO.NET installé n’apparaîtront pas ici, mais vous pouvez toujours y connecter par programmation.

## <a name="add-a-connection-in-server-explorer"></a>Ajouter une connexion dans l’Explorateur de serveurs

Pour créer une connexion à la base de données, cliquez sur le **ajouter une connexion** icône dans **Explorateur de serveurs**, ou avec le bouton droit dans **Explorateur de serveurs** sur la **données Connexions** nœud et sélectionnez **ajouter une connexion**. À ce stade, vous pouvez également vous connecter à une base de données sur un autre serveur, un service SharePoint ou un service Azure.

![Icône de nouvelle connexion de l’Explorateur de serveur](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Ceci fait apparaître la **ajouter une connexion** boîte de dialogue. Ici, nous avons entré le nom de l’instance de SQL Server LocalDB.

![Ajouter une nouvelle connexion](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Modifier le fournisseur

Si la source de données n’est pas ce que vous souhaitez, cliquez sur le **modification** pour choisir une source de données et/ou un nouveau fournisseur de données ADO.NET. Le nouveau fournisseur peut demander vos informations d’identification, en fonction de sa configuration.

![Fournisseur de données de modification AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Tester la connexion

Une fois que vous avez choisi la source de données, cliquez sur **tester la connexion**. Si elle n’aboutit pas, vous devez résoudre les problèmes en fonction de la documentation du fournisseur.

![Tester la connexion](../data-tools/media/raddata-test-connection.png)

Si le test réussit, vous êtes prêt à créer un *source de données*, qui est un terme de Visual Studio signifie en réalité un *modèle de données* qui repose sur la base de données ou le service sous-jacent.

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
