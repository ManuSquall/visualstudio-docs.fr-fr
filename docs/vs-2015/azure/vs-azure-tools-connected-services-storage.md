---
title: Ajouter du stockage Azure à l’aide des Services connectés dans Visual Studio | Microsoft Docs
description: Ajouter le stockage Azure à votre application à l’aide de la boîte de dialogue Ajouter des Services connectés Visual Studio
author: ghogen
manager: douge
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 63b796d9c514602a40f15b5725c07b1b89787df1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001704"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Ajout de stockage Azure à l’aide des Services connectés Visual Studio
Avec Visual Studio, vous pouvez connecter les éléments suivants dans le stockage Azure à l’aide de la **ajouter des Services connectés** boîte de dialogue :

- C#service cloud
- Service mobile principal .NET
- Site Web ASP.NET ou service
- Service ASP.NET Core
- Service de tâche Web Azure 

La fonctionnalité service connecté ajoute toutes les références nécessaires et code de connexion à votre projet et modifie vos fichiers de configuration de manière appropriée. 

Une fois terminé, le **ajouter des Services connectés** automatiquement, boîte de dialogue affiche la documentation décrivant les étapes nécessaires pour commencer à travailler avec le stockage blob, files d’attente et tables.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Se connecter au stockage Azure à l’aide de la boîte de dialogue Services connectés
1. Ouvrez votre projet dans Visual Studio

1. Dans **l’Explorateur de solutions**, avec le bouton droit le **Services connectés** nœud, puis dans le menu contextuel, puis sélectionnez **ajouter un Service connecté**.
   
    ![Ajouter Azure service connecté](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Dans le **Services connectés** page, sélectionnez **stockage Cloud avec stockage Azure**.
   
    ![Ajouter le stockage Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Dans le **stockage Azure** boîte de dialogue, sélectionnez un compte de stockage existant, puis sélectionnez **ajouter**.
   
    Si vous avez besoin créer un compte de stockage, accédez à l’étape suivante. Sinon, passez à l’étape 6.
    
    ![Ajouter un compte de stockage existant au projet](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Pour créer un compte de stockage : 
   
   1. Sélectionnez **créer un compte de stockage** en bas de la boîte de dialogue.

   1. Remplissez le **créer un compte de stockage** boîte de dialogue, puis sélectionnez **créer**.
      
       ![Nouveau compte de stockage Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)
      
   1. Lorsque le **stockage Azure** boîte de dialogue s’affiche, le nouveau compte de stockage apparaît dans la liste. Sélectionnez le nouveau compte de stockage dans la liste, puis sélectionnez **ajouter**.

1. Le stockage de service connecté s’affiche sous le **références de Service** nœud de votre projet.
   
## <a name="how-your-project-is-modified"></a>Comment votre projet est modifié
Lorsque vous avez terminé la boîte de dialogue, Visual Studio ajoute des références et modifie certains fichiers de configuration. Les modifications spécifiques varient selon le type de projet : 

- Projet ASP.NET - [que s’est-il passé – projets ASP.NET](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- Projet ASP.NET Core - [que s’est-il passé – projets ASP.NET 5](http://go.microsoft.com/fwlink/p/?LinkId=513124) 
- Projet de service cloud (rôles web et worker) - [que s’est-il passé – projets de Service Cloud](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- Projet de tâche Web - [que s’est-il passé - projets de tâche Web](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Étapes suivantes
- [Forum MSDN : Le stockage Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog de l’équipe stockage Microsoft Azure](http://blogs.msdn.com/b/windowsazurestorage/)
- [Documentation d’Azure Storage](https://docs.microsoft.com/azure/storage/)
