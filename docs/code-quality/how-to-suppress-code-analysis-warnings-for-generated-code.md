---
title: "Comment&#160;: supprimer les avertissements d&#39;analyse du code pour du code g&#233;n&#233;r&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: supprimer les avertissements d&#39;analyse du code pour du code g&#233;n&#233;r&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les compilateurs de code managé génèrent souvent un code qui est ajouté à un projet pour faciliter le développement de code rapide.  De plus, les développeurs utilisent souvent des outils tiers afin de développer rapidement des applications.  Ces outils génèrent également un code qui est ajouté au projet.  
  
 Vous pouvez souhaiter consulter les violations de règle que l'analyse du code découvre dans le code généré.  Toutefois, vous pouvez souhaiter ne pas les consulter si vous ne pouvez pas afficher et gérer le code qui contient la violation.  
  
 La case à cocher **Supprimer les résultats du code généré** sur la page de propriétés Analyse du code d'un projet vous permet de choisir si vous souhaitez ou non consulter les avertissements d'analyse du code générés par un outil tiers.  
  
> [!NOTE]
>  Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles.  Vous pouvez afficher et maintenir le code source pour un formulaire ou un modèle.  
  
### Pour supprimer des avertissements pour le code généré dans un projet  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.  
  
2.  Cliquez sur **Analyse du code**.  
  
3.  Activez la case à cocher **Supprimer les résultats du code généré**.