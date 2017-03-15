---
title: "Espion express, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.Quickwatch (commande)"
  - "Espion express (commande)"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Espion express, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Affiche le texte sélectionné ou spécifié dans le champ Expression de la [boîte de dialogue Espion express](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md).  Vous pouvez utiliser cette boîte de dialogue pour calculer la valeur actuelle d'une variable ou expression reconnue par le débogueur, ou le contenu d'un Registre.  De plus, vous pouvez modifier la valeur de toute variable non constante ou le contenu de tout Registre.  
  
## Syntaxe  
  
```  
Debug.QuickWatchq [text]  
```  
  
## Arguments  
 `text`  
 Facultatif.  Texte à ajouter dans la boîte de dialogue **Espion express**.  
  
## Notes  
 Si l'argument `text` est omis, le texte ou mot sélectionné au niveau du curseur est ajouté par défaut dans la fenêtre Espion.  
  
## Exemple  
  
```  
>Debug.QuickWatch  
```  
  
## Voir aussi  
 [Comment : utiliser la boîte de dialogue Espion express](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)