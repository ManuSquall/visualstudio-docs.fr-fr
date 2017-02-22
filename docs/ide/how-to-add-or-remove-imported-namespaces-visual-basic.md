---
title: "Comment&#160;: ajouter ou supprimer des espaces de noms import&#233;s (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ajouter des espaces de noms importés"
  - "espaces de noms importés (Visual Studio)"
  - "espaces de noms (Visual Studio), importés"
  - "références (Visual Studio), espaces de noms importés"
  - "supprimer des espaces de noms importés"
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Comment&#160;: ajouter ou supprimer des espaces de noms import&#233;s (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous importez un espace de noms, vous pouvez utiliser certains de ses éléments dans votre code, sans toutefois les qualifier entièrement.  Par exemple, si vous voulez accéder à la méthode `Create` de la classe `System.Messaging.MessageQueue`, vous pouvez importer l'espace de noms `System.Messaging` et faire juste référence à l'élément dont vous avez besoin dans le code comme `MessageQueue.Create`.  
  
 Les espaces de noms importés sont gérés sur la page **Références** du **Concepteur de projets**.  Les importations spécifiées dans cette boîte de dialogue sont passées directement au compilateur \(`/imports`\) et s'appliquent à tous les fichiers de votre projet.  L'instruction `Imports` vous permet d'utiliser un espace de noms dans un seul fichier de code source.  
  
### Pour ajouter un espace de noms importé  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur le nœud **My Project** du projet.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l'onglet **Références**.  
  
3.  Dans la liste **Espaces de noms importés**, activez la case à cocher de l'espace de noms que vous souhaitez ajouter.  
  
    > [!NOTE]
    >  Pour être importé, l'espace de noms doit se trouver dans un composant référencé.  Si l'espace de noms n'apparaît pas dans la liste, vous devrez ajouter une référence au composant qui le contient.  Pour plus d'informations, consultez [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
### Pour supprimer un espace de noms importé  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur le nœud **My Project** du projet.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l'onglet **Références**.  
  
3.  Dans la liste **Espaces de noms importés**, désactivez la case à cocher de l'espace de noms que vous souhaitez supprimer.  
  
## Importations utilisateur  
 Les importations utilisateur vous permettent d'importer une classe spécifique au sein un espace de noms plutôt que l'espace de noms tout entier.  Par exemple, votre application peut avoir une importation concernant l'espace de noms `Systems.Diagnostics`, mais la seule classe qui vous intéresse dans cet espace de noms est la classe `Debug`.  Vous pouvez définir `System.Diagnostics.Debug` comme une importation utilisateur, puis supprimer l'importation de `System.Diagnostics`.  
  
 Si vous changez ensuite d'avis et décidez que vous avez besoin de la classe `EventLog`, vous pouvez indiquer `System.Diagnostics.EventLog` comme importation utilisateur et remplacer `System.Diagnostics.Debug` à l'aide de la fonctionnalité de mise à jour.  
  
#### Pour ajouter une importation utilisateur  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur le nœud **My Project** du projet.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l'onglet **Références**.  
  
3.  Dans la zone de texte sous la liste **Espaces de noms importés**, indiquez le nom complet de l'espace de noms que vous voulez importer, y compris l'espace de noms racine.  
  
4.  Cliquez sur le bouton **Ajouter une importation utilisateur** pour ajouter l'espace de noms à la liste **Espaces de noms importés**.  
  
    > [!NOTE]
    >  Le bouton **Ajouter une importation utilisateur** sera désactivé si l'espace de noms correspond déjà à un dans la liste, car vous ne pouvez pas ajouter deux fois une importation.  
  
#### Pour mettre à jour une importation utilisateur  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur le nœud **My Project** du projet.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l'onglet **Références**.  
  
3.  Dans la liste **Espaces de noms importés**, sélectionnez l'espace de noms que vous voulez changer.  
  
4.  Dans la zone de texte sous la liste **Espaces de noms importés**, indiquez le nom du nouvel espace de noms.  
  
5.  Cliquez sur le bouton **Mettre à jour l'importation utilisateur** pour mettre à jour l'espace de noms dans la liste **Espaces de noms importés**.  
  
## Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)