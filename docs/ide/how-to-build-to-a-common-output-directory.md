---
title: "Comment&#160;: g&#233;n&#233;rer un r&#233;pertoire de sortie commun | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "générations (Visual Studio), répertoire commun"
  - "répertoire commun"
  - "répertoire de sortie"
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Comment&#160;: g&#233;n&#233;rer un r&#233;pertoire de sortie commun
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère chaque projet dans une solution dans son propre dossier à l'intérieur de la solution.  Vous pouvez modifier les chemins de sortie de génération de vos projets pour imposer que toutes les sorties soient placées dans le même dossier.  
  
### Pour placer toutes les sorties de solution dans un répertoire commun  
  
1.  Cliquez sur un projet dans la solution.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
3.  Selon le type de projet, cliquez sur l'onglet **Compiler** ou **Générer**, puis définissez le **Chemin de sortie** à un dossier à utiliser pour tous les projets de la solution.  
  
4.  Répétez les étapes 1 à 3 pour tous les projets de la solution.  
  
## Voir aussi  
 [Génération d'applications dans Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Comment : modifier le répertoire de sortie de la génération](../ide/how-to-change-the-build-output-directory.md)