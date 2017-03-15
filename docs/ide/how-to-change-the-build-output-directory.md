---
title: "Comment&#160;: modifier le r&#233;pertoire de sortie de la g&#233;n&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "répertoire de sortie, modifier"
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: modifier le r&#233;pertoire de sortie de la g&#233;n&#233;ration
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez spécifier l’emplacement de sortie en fonction de la configuration \(débogage, version ou les deux\) généré par votre projet.  
  
> [!NOTE]
>  Si vous possédez un **projet d’installation**, lisez la remarque à la fin de cet article.  
  
## Modification du répertoire de sortie de génération  
  
#### Pour modifier le répertoire de sortie de génération  
  
1.  Dans la barre de menus, choisissez **Projet**, *Propriétés***Nom\_app**. Vous pouvez également cliquer avec le bouton droit sur le nœud du projet dans l'**Explorateur de solutions**, puis sélectionner **Propriétés**.  
  
2.  Si vous avez un projet Visual Basic, sélectionnez l'onglet **Compiler**. Si vous avez un projet Visual C\#, sélectionnez l'onglet **Générer**. Si vous avez un projet C\+\+ ou un projet JavaScript, sélectionnez l'onglet **Général**.  
  
3.  Dans la liste déroulante de configuration située dans la partie supérieure, choisissez la configuration pour laquelle vous voulez modifier l’emplacement du fichier de sortie \(débogage, version ou tout\).  
  
     Recherchez l'entrée de chemin de sortie \(**Chemin de sortie de la génération** en Visual Basic, **Répertoire de sortie** en Visual C\+\+, **Chemin de sortie** en JavaScript et C\#\). Spécifiez un nouveau répertoire de sortie de génération relatif au répertoire du projet.  
  
> [!NOTE]
>  Dans un projet d’installation, la zone **Nom du fichier de sortie** permet uniquement de modifier l’emplacement du fichier Setup.exe, et non l’emplacement des fichiers du projet. Pour plus d'informations, consultez **Build, propriétés de configuration, boîte de dialogue Propriétés du projet de déploiement**.  
  
## Voir aussi  
 [Générer, page du Concepteur de projets \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)   
 [Général, page de propriétés \(Projet\)](/visual-cpp/ide/general-property-page-project)   
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)