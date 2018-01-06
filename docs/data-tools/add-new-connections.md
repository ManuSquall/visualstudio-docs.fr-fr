---
title: Ajouter de nouvelles connexions | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 26a45e8fe44e2e0945a105711ae84b1082d5c891
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="add-new-connections"></a>Ajouter de nouvelles connexions

Vous pouvez tester votre connexion à une base de données ou un service et Explorer le contenu de la base de données et des schémas, à l’aide de **l’Explorateur de serveurs**, **Cloud Explorer**, ou **l’Explorateur d’objets SQL Server**. La fonctionnalité de ces fenêtres se chevauche dans une certaine mesure. Les principales différences sont :

- Explorateur de serveurs

   Installé par défaut dans Visual Studio. Peut être utilisé pour tester les connexions et afficher les bases de données SQL Server, toutes les autres bases de données ayant un fournisseur ADO.NET installé et certains services Azure. Montre également les objets de bas niveau tels que les compteurs de performances système, les journaux des événements et les files d’attente. Si une source de données n’a aucun fournisseur ADO.NET, il ne s’afficheront ici, mais vous pouvez toujours l’utiliser à partir de Visual Studio en vous connectant par programme.

- Cloud Explorer

   Cette fenêtre installer manuellement comme une extension Visual Studio en sélectionnant **outils**, **Extensions et mises à jour**, **Online**, **Visual Studio Markeplace**. Fournit des fonctionnalités spécialisées pour l’exploration et la connexion aux services Azure.

- Explorateur d'objets SQL Server

   Installé avec SQL Server Data Tools et visibles sous le **vue** menu. Si vous n’apparaît pas, accédez à **programmes et fonctionnalités** dans le panneau de configuration, recherchez Visual Studio, puis sélectionnez **modification** exécuter à nouveau le programme d’installation après avoir sélectionné la case à cocher pour SQL Server Data Tools. Utilisez **l’Explorateur d’objets SQL Server** à l’affichage des bases de données SQL (s’ils ont un fournisseur ADO.NET), créer de nouvelles bases de données, de modifier des schémas, de créer des procédures stockées, de récupérer les chaînes de connexion, d’afficher les données et bien plus encore. Les bases de données SQL qui aucun fournisseur ADO.NET est installé n’apparaîtront pas ici, mais vous pouvez toujours vous connecter à leur par programme.

## <a name="add-a-connection-in-server-explorer"></a>Ajouter une connexion dans l’Explorateur de serveurs

Pour créer une connexion à la base de données, cliquez sur le **ajouter une connexion** icône dans **l’Explorateur de serveurs**, ou avec le bouton droit dans **l’Explorateur de serveurs** sur la **données Connexions** nœud et sélectionnez **ajouter une connexion**. À ce stade, vous pouvez également vous connecter à une base de données sur un autre serveur, un service SharePoint ou un service Azure.

![Icône d’Explorer la nouvelle connexion serveur](../data-tools/media/raddata-server-explorer-new-connection-icon.png "icône de nouvelle connexion de serveur Explorer raddata")

Ceci fait apparaître la **ajouter une connexion** boîte de dialogue. Ici, nous avons entré le nom de l’instance de base de données SQL Server locale.  

![Ajouter une nouvelle connexion](../data-tools/media/raddata-add-new-connection-dialog.png "raddata boîte de dialogue Ajouter nouvelle connexion")  

## <a name="change-the-provider"></a>Modifier le fournisseur

Si la source de données n’est pas ce que vous souhaitez, cliquez sur le **modification** pour choisir une source de données et/ou un nouveau fournisseur de données ADO.NET. Le nouveau fournisseur peut demander vos informations d’identification, en fonction de leur configuration.

![Modifier le fournisseur de données AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png "raddata AD0.NET modification du fournisseur de données")

## <a name="test-the-connection"></a>Tester la connexion

Une fois que vous avez choisi la source de données, cliquez sur **tester la connexion**. S’il ne réussit pas, vous devez résoudre les problèmes en fonction de la documentation du fournisseur.

![Tester la connexion](../data-tools/media/raddata-test-connection.png "raddata tester la connexion")

Si le test réussit, vous êtes prêt à créer un *source de données*, qui est un terme de Visual Studio signifie en réalité un *modèle de données* qui est basé sur la base de données sous-jacente ou le service.

## <a name="see-also"></a>Voir aussi

[Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)