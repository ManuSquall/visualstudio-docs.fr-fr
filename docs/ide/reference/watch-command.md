---
title: "Espion, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch (commande)"
  - "Espion (commande)"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Espion, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crée et ouvre une instance spécifiée d'une fenêtre **Espion**.  Vous pouvez utiliser une fenêtre **Espion** pour calculer les valeurs des variables, des expressions et des registres, modifier ces valeurs et enregistrer les résultats.  
  
## Syntaxe  
  
```  
Debug.Watch[index]  
```  
  
## Arguments  
 `index`  
 Obligatoire.  Le numéro d'instance de la fenêtre Espion.  
  
## Notes  
 L'`index` doit être un entier.  Les valeurs valides sont 1, 2, 3 ou 4.  
  
## Exemple  
  
```  
>Debug.Watch1  
```  
  
## Voir aussi  
 [Fenêtres Variables locales et Automatique](../../debugger/autos-and-locals-windows.md)   
 [Comment : modifier une valeur dans une fenêtre de variable](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [Comment : utiliser la boîte de dialogue Espion express](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)