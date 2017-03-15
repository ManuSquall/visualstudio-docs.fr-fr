---
title: "Comment&#160;: cr&#233;er plusieurs configurations simultan&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er plusieurs configurations simultan&#233;ment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez générer la plupart des types de projets avec une partie ou même l'ensemble des configurations de build en même temps à l'aide de la boîte de dialogue **Générer en tâche de fond**.  Toutefois, vous ne pouvez pas générer les types de projets suivants dans plusieurs configurations de build en même temps :  
  
1.  Applications du [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] générées pour Windows à l'aide de JavaScript.  
  
2.  Tous les projets Visual Basic.  
  
 Pour plus d'informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).  
  
### Pour générer un projet dans plusieurs configurations de build  
  
1.  Dans la barre de menus, sélectionnez **Build**, **Générer en tâche de fond**.  
  
2.  Dans la colonne **Build**, cochez les cases des configurations dans lesquelles vous souhaitez générer un projet.  
  
    > [!TIP]
    >  Pour modifier ou créer une configuration de build pour une solution, choisissez **Build**, **Gestionnaire de configurations** dans la barre de menus pour ouvrir la boîte de dialogue **Gestionnaire de configurations**.  Après avoir modifié une configuration de build pour une solution, choisissez le bouton **Régénérer** dans la boîte de dialogue **Générer en tâche de fond** pour mettre à jour toutes les configurations de build pour les projets de la solution.  
  
3.  Choisissez le bouton **Build** ou **Régénérer** pour générer le projet avec les configurations que vous avez spécifiées.  
  
## Voir aussi  
 [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)   
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)